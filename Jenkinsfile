pipeline {
  environment {
    registry = "rangusrikanth/bwce"
    registryCredential = 'dockerhub'
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
          docker.withRegistry( 'https://hub.docker.com/repository/docker/rangusrikanth', dockerhub ) {
            app.push("${env.BUILD_NUMBER}")
             app.push("latest")
          }
        }
      }
    }
  }
}
