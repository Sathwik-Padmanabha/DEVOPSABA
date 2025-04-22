pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'sathwikpadmanabha/devopsaba:latest'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Sathwik-Padmanabha/DEVOPSABA.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Docker Build and Push') {
            steps {
                script {
                    sh 'docker build -t myapp .'
                    sh 'docker push sathwikpadmanabha/devopsaba:latest'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deployment steps, like pulling the Docker image and running it on a server
                }
            }
        }
    }

    post {
        always {
            // Send email notification after build completion
            emailext subject: "Build Status: ${currentBuild.currentResult}",
                     body: "The build completed with status: ${currentBuild.currentResult}",
                     to: "sathwikpadmanabha@gmail.com"
        }
    }
}
