pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t incident-recovery-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f incident-recovery-app || true
                docker run -d --name incident-recovery-app -p 8080:80 incident-recovery-app
                '''
            }
        }
    }
}