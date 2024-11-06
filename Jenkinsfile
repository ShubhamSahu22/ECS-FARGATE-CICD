pipeline {

         agent any 
         
         Tools { 
             nodejs 'NodeJS'
             
          }       
         


         
               stages {
                   stage('github'){
              steps {
                        git branch: 'main', credentialsId: 'git-docker-nodejs', url: 'https://github.com/ShubhamSahu22/ECS-FARGATE-CICD.git'
                      } 
                 }
                 stage {
                      steps('install node dependency') {

                       steps {
                            sh 'npm install'    
                       
                         }     
              
                   }
                    stage('test case') {
                              steps {
                                 sh 'npm test'

                        }  

                   } 


            }            
   
}     
