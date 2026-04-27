pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/ange0423/python-docker-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t python-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    docker rm -f python-app-container || true
                    docker run -d -p 5000:8080 --name python-app-container python-app
                '''
            }
        }
    }
}