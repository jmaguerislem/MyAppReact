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
                sh 'docker build -t mern-server ./server'
                sh 'docker build -t mern-client ./client'
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