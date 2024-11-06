pipeline {

         agent any 
         
               stages {
                   stage('github'){
              steps {
                        git branch: 'main', credentialsId: 'git-docker-nodejs', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
                      } 
                 }
         
}  
