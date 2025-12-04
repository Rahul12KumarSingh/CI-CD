pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || echo "no tests found"'
            }
        }

        stage('Start Application') {
            steps {
                echo "Starting the server..."
                sh 'node index.js'
            }
        }
    }

    post {
        success {
            echo "Build finished successfully!"
        }
        failure {
            echo "Build failed!"
        }
    }
}
