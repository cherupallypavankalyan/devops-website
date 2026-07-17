pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-website:v2 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat '''
                docker stop devops-web
                docker rm devops-web
                exit /b 0
                '''
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d --name devops-web -p 8080:80 devops-website:v2'
            }
        }
    }
}