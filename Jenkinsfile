pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'sudo docker build -t myapp .'
            }
        }

        stage('Test') {
            steps {
                echo 'Checking Docker containers...'
                sh 'sudo docker ps'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application container...'
                sh 'sudo docker rm -f myapp-container || true'
                sh 'sudo docker run -d -p 8081:80 --name myapp-container myapp'
            }
        }
    }
}
