pipeline {
  environment {
    registry = "rangusrikanth/sagest"
    registryCredential = 'dockerhub'
    dockerImage = 'rangusrikanth/sagest:latest'
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
          docker.withRegistry( 'srikanthrangu', dockerhub ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
