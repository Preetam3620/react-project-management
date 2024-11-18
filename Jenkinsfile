pipeline {
    agent any

    environment {
        NODE_ENV = 'development' 
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Preview') {
            steps {
                sh 'npm run preview'
            }
        }
        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'build/**/*', fingerprint: true
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
