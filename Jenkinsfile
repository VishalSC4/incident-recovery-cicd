pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/<YOUR_USERNAME>/incident-recovery-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t incident-recovery-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f app || true
                docker run -d -p 80:80 --name app incident-recovery-app
                '''
            }
        }
    }
}