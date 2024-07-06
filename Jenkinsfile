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
                dir('user-management') {
                    // Ejecutar npm install dentro de user-management
                    sh 'npm install'
                }
            }
        }
        stage('Run Tests') {
            steps {
                dir('user-management') {
                    // Ejecutar npm test dentro de user-management
                    sh 'npm test'
                }
            }
        }
        // Otras etapas de tu pipeline aquí
    }
}