pipeline {
              agent any 
              tools {
                  nodejs 'NodeJS'i
               }
               stages{
                        stage('github') {
                               steps {
                                  git branch: 'main', credentialsId: 'jen-git-dind', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
                               }
                     }
                      stage('unit Test'){
                         steps {
                                 sh 'npm test'
                                 sh 'npm install'
		     } 

               }


     }


}
