pipeline {
  environment {
    registry = "rangusrikanth/bwce"
    registryCredential = 'dockerhub'
    dockerImage= ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git branch: 'main', credentialsId: 'github', url: 'https://github.com/rangusrikanth/Docker-test.git'
      }
    }
    stage('Building image') {
      steps{
        script {
            dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
            dockerImage.push('latest')
          }
        }
      }
    }
  }
}
