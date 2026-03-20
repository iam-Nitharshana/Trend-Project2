pipeline {
    agent any

    stages {
    

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nitharshana9490/trend-app .'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push nitharshana9490/trend-app'
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
