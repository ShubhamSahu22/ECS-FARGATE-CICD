pipeline {  
         agent any
         tools {
                nodejs 'NodeJS'
         }
         environment {
                   SONAR_PROJECT_KEY= complete ECS_FARAGATE_PIPELIENE
                   SONAR_SCANNER_HOME= tool 'SonarQubeScanner'


         }
         stages  {
                  stage('gitHub'){
                          steps {
                                  git branch: 'main', credentialsId: 'jen-git-dind', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
                         }
               }
               stage('Unit Test'){
                       steps {
                            sh 'npm test'
                            sh 'npm install'
                       }
     
                }
                stage('SonarQube  analysis'){
                        steps { 
                              withCredentials([string(credentialsId: 'ECS_FARGATE_CICD', variable: 'Sonar_token')]) {
                                                withSonarQubeEnv('SonarQube') {
                                                sh """
                                                ${SONAR_SCANNER_HOME}/bin/sonar-scanner \
                                                 -Dsonar.projectKey='${SONAR_PROJECT_KEY}' \
                                                 -Dsonar.sources='.' \
                                                 -Dsonar.host.url='http://sonarqube-dind:9000' \
                                                 -Dsonar.login='${SONAR_TOKEN}'
                                                 """


                                        }
                                }
                       
                       } 
               
               } 
           
        } 

}
