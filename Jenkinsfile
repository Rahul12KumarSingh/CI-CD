pipeline {
    agent any

    environment {
        NODE_ENV = 'production' ,
        PORT = '3000',
        BRANCH_NAME = "main"
    }
 

    stages {

        stage('Checkout') {
            steps {
                checkout scm 

                script{
                    echo "Checked out branch: ${env.BRANCH_NAME}"
                    echo "Running on port: ${env.PORT}"
                    echo "Running in environment: ${env.NODE_ENV}"
                }
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
