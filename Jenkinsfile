pipeline {
    agent any

    stages {
        

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nitharshana9490/trend-app1 .'
            }
        }
         
        stage('Push to DockerHub') {
            steps {
                sh 'docker login -u nitharshana9490 -p $password'
                sh 'docker push nitharshana9490/trend-app1'
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
