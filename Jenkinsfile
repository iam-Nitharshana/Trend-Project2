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
                script {
                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'AWS']]) {     
                sh 'aws eks --region ap-south-1 update-kubeconfig --name trend-cluster'
                sh 'kubectl apply -f deployment.yml --validate=false'
                sh 'kubectl apply -f service.yml'
                    }
                }
            }
        }
    }
}
