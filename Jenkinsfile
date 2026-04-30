pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/muddasir-x/CI-CD-Pipeline-with-Docker.git'
            }
        }

        stage('Install Dependencies (Node in Docker)') {
            agent {
                docker {
                    image 'node:18-slim'
                }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Cleanup Old Container') {
            steps {
                sh 'docker rm -f devops-app || true'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app:${BUILD_NUMBER} .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name devops-app devops-app:${BUILD_NUMBER}'
            }
        }
    }

    post {
        always {
            echo "Pipeline executed"
        }
        success {
            echo "Pipeline successful ✅"
        }
        failure {
            echo "Something went wrong ❌"
        }
    }
}
