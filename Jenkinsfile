pipeline {
    agent any
    stages {
         stage('Init') {
            agent {
                docker
            }
            steps {
                sh 'docker rm -f $(docker ps -qa) || true'
            }
        }
        stage('Build') {
            agent {
                dockers
            }
            steps {
                sh 'docker build -t myapp .'
            }
        }
        stage('Deploy') {
            agent {
                docker
            }
            steps {
                sh 'docker run -d -p 80:5500 --name myapp myapp:latest'
            }
        }
    }
}