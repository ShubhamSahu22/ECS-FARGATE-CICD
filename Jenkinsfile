pipeline {
    agent any
    tools {
        nodejs 'NodeJS'
    }
    environment {
        SONAR_PROJECT_KEY = 'ECS-Pipeline'
        SONAR_SCANNER_HOME = 'SonarQubeScanner' // Ensure that this is configured correctly in Jenkins Global Tool Configuration
    }
    stages {
        stage('github checkout') {
            steps {
                git branch: 'main', credentialsId: 'git-docker-nodejs', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
            }
        }
        stage('Unit Test') {
            steps {
                sh 'npm install'
                sh 'npm test'
              }
        }       
        
        stage('SonarQube Analysis') {
            steps {
                withCredentials([string(credentialsId: 'ECS_FARGATE-Token', variable: 'SONAR_TOKEN')]) {
                    withSonarQubeEnv('SonarQube') {
                        sh '''$SONAR_SCANNER_HOME/bin/sonar-scanner \
                            -Dsonar.projectKey=ECS_Pipeline \
                            -Dsonar.sources=. \
                            -Dsonar.host.url=http://http://54.204.213.9:9000/ \
                            -Dsonar.login=$SONAR_TOKEN'''
                    }
                }
            }
        }
    }
}
