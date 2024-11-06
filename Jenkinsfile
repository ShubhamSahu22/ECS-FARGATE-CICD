pipeline {
    agent any

    tools {
        nodejs 'NodeJS' // Ensure NodeJS is configured in Jenkins
    }
     environment { 
              SONAR_PROJECT_KEY = 'ECS-Pipeline'
              SONAR_SCANNER_HOME = 'SonarQubeScanner'

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
        stage('SonarQube Analysis') {
             steps {
                 withCredentials([string(credentialsId: 'ECS-Pipeline-token', variable: 'SONAR_TOKEN')]) {
    
                               withSonarQubeEnv('SonarQube') {
                                                   sh """
                                                   ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
                                                    -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                                                    -Dsonar.sources=. \
                                                    -Dsonar.host.url= http://54.161.74.191:9000 \
                                                    -Dsonar.login=${SONAR_TOKEN} \
                                                    """

                                          }


                             }    
           
                            
                  }
 

        }

    }
}

                  
