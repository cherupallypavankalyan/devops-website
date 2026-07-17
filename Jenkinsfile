pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-website:v2 .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker stop devops-web || exit 0'
                bat 'docker rm devops-web || exit 0'
                bat 'docker run -d -p 8080:80 --name devops-web devops-website:v2'
            }
        }
    }
}