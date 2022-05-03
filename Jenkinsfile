pipeline {
  agent any
  environment {
    registry = "sandeepwalvekar/devsecops1"
    registryCredential = "sandeepwalvekar"
    dockerImage = ''
  }
  stages{
    stage('Build Docker Image'){
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    
    stage('Push Image to Docker repo'){
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push() 
          }
        }
        
      }
    }
    stage('Test Image'){
      steps{
        sh 'docker run -d -p 8000:80 $registry:$BUILD_NUMBER'
      }
    }
  }
}
