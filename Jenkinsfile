pipeline {
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                git url: 'https://github.com/rangusrikanth/Docker-test.git',branch: 'main',
                credentialsId: 'GitHub-crds'
            }
        }

        stage('Building image') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
    }
}
