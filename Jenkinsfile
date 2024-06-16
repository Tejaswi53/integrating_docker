pipeline {
    agent any  // Adjust if you need a specific agent (e.g., label)
     environment {
        // Define environment variables for Docker Hub credentials
        DOCKER_HUB_USERNAME = credentials('tejaswimedisetti')
        DOCKER_HUB_PASSWORD = credentials('shashiteja@3028')
                // Define any other environment variables needed
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', // Replace with your branch name
                    url: 'https://github.com/Tejaswi53/integrating_docker.git' // Replace with your Git repository URL
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t tejajenkins .' // Replace with your image name
            }
        }
        stage('Run Tests (Optional)') {
            steps {
                script {
                    // Customize testing commands based on your framework and container environment
                    bat 'docker run -d --name cont2 -p 8002:80 tejajenkins'
                }
            }
        }
        stage('Deploy Image (Optional)') {
            steps {
                script {
                    // Securely store Docker registry credentials in Jenkins Credentials Management
                   
                       docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        // Push the Docker image to Docker Hub
                        bat 'docker tag tejajenkins tejaswimedisetti/tejajenkinsrepo'
                        bat 'docker push tejaswimedisetti/tejajenkinsrepo'
                    
                    }
                }
            }
        }
    }


}
