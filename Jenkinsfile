pipeline {

         agent any 
         tools {
              nodejs 'NodeJS'
            
               stages {
                   stage('github'){
                     steps {
                           git branch: 'main', credentialsId: 'git-docker-nodejs', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
                      } 

                  }
                   stage('install node dependency') {
                         steps {
                                sh 'npm install'
                          }                
                           
                       }    
                       stage('Test case'){
                         steps { 

                               sh 'npm test'
                         }
                 
                    } 
                    stage('Build Docker Images') {
                         steps {
                                 script { 
                                       docker.build("nodeimage"+"$BUILD_NUMBER")
                             }
                        } 
                 }          

  
           }

           post {
                   success { 
                           echo 'Build completed succesfully!'
                             
                  }
                  failure {
                          echo 'Build failed. check logs.'

                 }  
          
          } 
            
}
