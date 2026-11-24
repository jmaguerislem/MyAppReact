pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build images') {
            steps {
                sh 'docker build -t mern-server ./Server'
                sh 'docker build -t mern-client ./Client'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }

        stage('Verify') {
            steps {
                sh 'docker compose ps'
            }
        }
    }
}