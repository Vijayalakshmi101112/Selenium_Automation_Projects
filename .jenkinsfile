pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Vijayalakshmi101112/Selenium_Automation_Projects.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-app:latest .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8080:8080 --name my-app-container my-app:latest'
                }
            }
        }

        stage('Post-Build Cleanup') {
            steps {
                script {
                    sh 'docker ps'
                }
            }
        }
    }

    post {
        always {
            script {
                sh 'docker stop my-app-container || true'
                sh 'docker rm my-app-container || true'
            }
        }
    }
}
