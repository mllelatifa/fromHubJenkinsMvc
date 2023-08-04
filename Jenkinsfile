pipeline {
    agent any

    tools {
        maven "Maven 3.9.2"
    }

    stages {

        stage('Maven Build') {
           steps {
                  bat 'mvn clean package'
           }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('demojenkinsmvc:latest')
                }
            }
        }
        stage('Deploy Docker Image') {
            steps {
                script {
                    try {
                        bat "docker stop demojenkinsmvc"
                        bat "docker rm demojenkinsmvc"
                    } catch (Exception e) {
                        echo '404 Not Found : demojenkinsmvc'
                    }
                    bat "docker run --name demojenkinsmvc -d -p 8075:8080 demojenkinsmvc:latest JenkinsMvc.jar"
                }
            }
        }
    }
}