pipeline {
  agent any
  stages{
    stage('Build Docker Image'){
      steps{
        sh 'docker build -t testprj:$BUILD_NUMBER'      
      }
   }
    stage('Test Image'){
      steps{
        sh 'docker run -d -p 8000:80 testprj:$BUILD_NUMBER'
      }
    }
  }
}
