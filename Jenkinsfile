pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gpttestx/myapp.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("myapp:latest")
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    dockerImage.run('-d -p 5000:5000')
                }
            }
        }
    }
}
