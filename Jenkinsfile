pipeline {
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                git url: 'https://github.com/rangusrikanth/Docker-test.git',branch: 'main',
                credentialsId: 'GitHub-crds'
            }
        }
           stage('Docker Build') {
        steps {
      	    sh 'docker build -t rangusrikanth/sagest:latest .'
        }
    }
}
}
