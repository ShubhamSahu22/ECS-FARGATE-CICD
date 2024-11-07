pipeline {
         agent any
         tools {
             nodejs 'NodeJS'
         }
          environment {
                 SONAR_PROJECT_KEY = 'ECS_Pipeline'
                 SONAR_SCANNER_HOME = 'SonarQubeScanner'    
                } 
                 stages {

                   stage('github checkout') {
             
                     steps {
                          git branch: 'main', credentialsId: 'git-docker-nodejs ', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
                        }

                  }    
                  stage('Node dependency') {
                        steps  { 
                            sh 'npm install'
                       }
                       

                    }
                     stage('Test case') { 
                      steps { 
                            sh 'npm test'        
                       }
               }
                 stage('SonarQube Analysis') {
                       steps { 
                            withCredentials([string(credentialsId: 'ECS_FARGATE-Token', variable: 'SONAR_TOKEN' { 

                                             withSonarQubeEnv('SonarQube') {
                                              sh '''SonarQubeScanner/bin/sonar-scanner \
                                                 -Dsonar.projectKey=ECS_Pipeline \
                                                 -Dsonar.sources=. \
                                                -Dsonar.host.url=http://sonarqube-dind:9000 \
                                                -Dsonar.login=$SONAR_TOKEN'''
                                     
                                            }

    
                                       }                             


                           }                             

                      }
               }                   
                   
         }

}
                   





