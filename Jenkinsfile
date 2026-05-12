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
    }
}