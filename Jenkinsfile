pipeline {
    agent any  // Adjust if you need a specific agent (e.g., label)
    environent {
        DOCKERHUB_CREDENTIALS = credentials('74e88eaa-c12e-4c73-b140-a6ebcec556e3')
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
                bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps {
                bat 'docker tag tejajenkins tejaswimedisetti/tejajenkinsrepo
                bat 'docker push tejaswimedisetti/tejajenkinsrepo
            }
        }
    }


}
