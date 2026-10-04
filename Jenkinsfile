pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/rj90996-eng/devops-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo:1.0 .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop devops-demo-container || true'
                sh 'docker rm devops-demo-container || true'
                sh 'docker run -d -p 5000:5000 --name devops-demo-container devops-demo:1.0'
            }
        }
    }
}