pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Tenssan/user-manangment-devops.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('user-management:latest')
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
                        docker.image('user-management:latest').push()
                    }
                }
            }
        }
        stage('Deploy to Test Environment') {
            steps {
                sh 'docker-compose -f docker-compose.test.yml up -d'
            }
        }
        stage('Deploy to Production Environment') {
            when {
                branch 'main'
            }
            steps {
                sh 'docker-compose -f docker-compose.prod.yml up -d'
            }
        }
    }
}