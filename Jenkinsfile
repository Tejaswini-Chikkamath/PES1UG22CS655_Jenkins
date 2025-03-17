pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'sudo apt update && sudo apt install -y g++'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'pwd && ls -l'  // Debugging step
                sh 'ls -l main'  // Check if hello.cpp is inside 'main/'
                sh 'g++ main/hello.cpp -o output'  // Compile from correct path
                echo 'Build Stage Successful'
            }
        }

        stage('Test') {
            steps {
                sh './output'  // Run compiled program
                echo 'Test Stage Successful'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment Successful'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
