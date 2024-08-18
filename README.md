# Node Todo App with CI/CD [![Visitors](https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fajitfawade%2Fnode-todo-cicd&countColor=%232ccce4&style=plastic&labelStyle=upper)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fajitfawade%2Fnode-todo-cicd)

This is a simple to-do app that uses Node.js, Express, and EJS. It also uses Jenkins and Docker Compose for continuous integration and deployment.

## Prerequisites

To run this app, you need to have:

- Git installed on your machine.
- Jenkins installed and running on your machine or server.
- Docker and Docker Compose installed on your machine or server.

## Steps

### Step 1: Clone the Repository

To clone the repository, open a terminal or command prompt and run the following command:

```bash
git clone https://github.com/ajitfawade/node-todo-cicd.git
```

This will create a folder named `node-todo-cicd` in your current directory.

### Step 2: Add a Webhook

To add a webhook, go to your GitHub repository and click on **Settings**. Then click on **Webhooks** and then on **Add webhook**.

Fill in the form as follows:

- Payload URL: Enter your Jenkins URL followed by `/github-webhook/`. For example, `http://example.com/github-webhook/`.
- Content type: Select `application/json`.
- Secret: Leave it blank.
- SSL verification: Select `Enable SSL verification` if your Jenkins URL uses HTTPS, otherwise select `Disable SSL verification`.
- Which events would you like to trigger this webhook?: Select `Just the push event`.
- Active: Check this box.

Click on **Add webhook** to create the webhook.

You can test the webhook by clicking on **Edit** and then on **Test**. You should see a green check mark indicating that the webhook was delivered successfully.

### Step 3: Deploy the App

To deploy the app, go to your Jenkins dashboard and click on **New Item**.

Enter a name for your job (e.g., Node Todo App) and select **Freestyle project**. Then click **OK**.

On the configuration page, you can add some descriptions for your job if you want.

Under **Source Code Management**, select **Git** and enter the repository URL: [https://github.com/ajitfawade/node-todo-cicd.git]. You can leave the other fields as default.

Under **Build Triggers**, select **GitHub hook trigger for GITScm polling**. This will enable the job to be triggered by GitHub webhooks.

Under **Build**, click on **Add build step** and select **Execute shell** (or **Execute Windows batch command** if you are using Windows). This will allow you to run any shell or batch command as part of your job.

In the text area that appears, enter the command `docker-compose up -d --build` to build and run the app using Docker Compose. The `-d` flag runs the container in detached mode and the `--build` flag forces a rebuild of the image if there are any changes.

Click **Save** to save your job.

Now, whenever you push any changes to your GitHub repository, your Jenkins job will be triggered automatically and deploy your app using Docker Compose.

You can also manually trigger your job by clicking on **Build Now** on your Jenkins dashboard.

You can see the status and details of your job under **Build History**. You can also click on **Console Output** to see the logs of your job.

You can verify that your app is running by going to your browser and typing `http://localhost:8000`. You should see a todo app where you can add, edit, and delete tasks.


#this is a comment for testing
