pipeline {
    agent any  // Adjust if you need a specific agent (e.g., label)
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker')
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
                bat 'docker build -t tejajenkins2 .' // Replace with your image name
            }
        }
        stage('Run Tests (Optional)') {
            steps {
                script {
                    // Customize testing commands based on your framework and container environment
                    bat 'docker run -d --name cont10 -p 8010:80 tejajenkins2'
                }
            }
        }
        stage('Deploy Image (Optional)') {
            steps {
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps {
                bat 'docker tag tejajenkins tejaswimedisetti/tejajenkinsrepo'
                bat 'docker push tejaswimedisetti/tejajenkinsrepo'
            }
        }
    }


}
