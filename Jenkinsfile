pipeline {
    agent any

    environment {
        // Define environment variables for Docker Hub credentials
        DOCKER_HUB_USERNAME = credentials('tejaswimedisetti')
        DOCKER_HUB_PASSWORD = credentials('shashiteja@3028')
        DOCKER_HUB_REPO = 'tejaswimedisetti/tejajenkinsrepo'
        // Define any other environment variables needed
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code repository (e.g., Git)
                git url: 'https://github.com/Tejaswi53/integrating_docker.git'
                
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image using Dockerfile
                script {
                    bat 'docker build -t tejajenkins .' // Replace with your image name
                    bat 'docker run -d --name contr1 -p 8001:80 tejajenkins:latest '
                      
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                // Log in to Docker Hub
                script {
                    docker.withRegistry('https://registry.hub.docker.com', '74e88eaa-c12e-4c73-b140-a6ebcec556e3') {
                        // Push the Docker image to Docker Hub
                       
                       bat 'docker tag tejajenkins tejaswimedisetti/tejajenkinsrepo'
                       bat 'docker push tejaswimedisetti/tejajenkinsrepo:latest'
                        
                    }
                }
            }
        }

        
    }

    post {
        success {
            echo 'Docker image build and push successful!'
        }
        failure {
            echo 'Docker image build and push failed!'
        }
    }
}
