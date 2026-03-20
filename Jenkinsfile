pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/iam-Nitharshana/Trend-Project2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t your-dockerhub-username/trend-app .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push your-dockerhub-username/trend-app'
            }
        }

        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yml'
                sh 'kubectl apply -f service.yml'
            }
        }
    }
}
