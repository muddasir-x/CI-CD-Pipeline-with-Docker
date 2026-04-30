pipeline {
    agent any 

    stages {
        stage ('Clone code') {
            stpes {
                git 'https://github.com/muddasir-x/CI-CD-Pipeline-with-Docker.git'
            }
        }
        stage('Install Dependencies') {
            stpes {
                sh 'npm install'
            }
        }
        stage('Build container') {
            steps {
                sh 'docker build -t devops-app:v1'
            }
        }
        stage('Run container') {
            steps{
                sh 'docker run -d -p 3000:3000 devops-app'
            }
        }
        
    }
    post {
        always {
            echo "we build pipeline"
        }
        success {
            echo "pipeline successfull"
        }
        fail {
            echo "try again something is worng"
        }
    }
}
