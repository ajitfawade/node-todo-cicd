pipeline {
    agent { label 'dev' }
     

    stages {

        stage ('Code') {
            steps {
                git url: 'https://github.com/ajitfawade/node-todo-cicd.git', branch: 'master'
                echo ' pull from master '
            }
        }
        
        stage ('Build & Test') {
            steps {
                echo 'Build & Test'
                sh 'docker build . -t ajitfawade14/node-todo-app:latest'
            }
        }
        
        
        stage ('Deploy') {
            steps {
                echo 'Deploying'
                echo 'done by me'
                sh 'docker-compose down && docker-compose up -d'
            }
        }

    }
}
