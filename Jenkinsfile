pipeline {
  environment {
    dockerimagename = "rawatshubham138/nodeapp"
    
  }
  
  agent any

  stages {

     stage('Checkout Source') {
      steps {
        git 'https://github.com/rawatshubham138/node_app.git'
      }
     }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }
      
        
    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhubcred'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
          dockerImage.push("${env.BUILD_NUMBER}")            
          dockerImage.push("latest")        
          }
        }
      }
    }

//     stage('Deploying App to Docker') {
//       steps {
//         script {
//           
//         }
//       }
//     }

  }

}
