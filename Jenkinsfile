pipeline {
    agent any

    tools {
        nodejs 'NodeJS' // Ensure NodeJS is configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'git-docker-nodejs', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
            }
        }
        stage('Install Node Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }
}

                  
