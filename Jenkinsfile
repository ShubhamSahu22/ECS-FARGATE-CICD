pipeline {  
         agent any
         tools {
                nodejs 'NodeJS'
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
           
         } 

}
