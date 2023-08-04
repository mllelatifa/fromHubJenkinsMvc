pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('demoJenkinsMvc:latest')
                }
            }
        }
    }
}