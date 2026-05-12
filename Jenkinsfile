pipeline {
    agent any

    environment {
        IMAGE_NAME = "bhatspranav7/python-pipeline-app"
    }

    stages {

        stage('Run Python App') {
            steps {
                bat 'python app.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Login to DockerHub') {
            steps {

                withCredentials([usernamePassword(
                    credentialsId: 'docker-credentials',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {

                    bat 'echo %PASS% | docker login -u %USER% --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push %IMAGE_NAME%'
            }
        }
    }
}