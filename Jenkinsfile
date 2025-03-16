pipeline {
    agent any  // Use the default agent

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.image('gcc:latest').inside {
                        sh 'pwd && ls -l'  // Debugging step
                        sh 'ls -l main'  // Check if hello.cpp is inside 'main/'
                        sh 'g++ main/hello.cpp -o output'  // Compile from correct path
                        echo 'Build Stage Successful'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    docker.image('gcc:latest').inside {
                        sh './output'  // Run compiled program
                        echo 'Test Stage Successful'
                    }
                }
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
