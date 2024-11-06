pipeline {


         agent any
         tools {
             nodejs 'NodeJS'
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
                   
                   
            }

}
                   
