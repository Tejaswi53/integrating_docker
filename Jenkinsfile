pipeline {
    agent any  
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker')
    }
     
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/Tejaswi53/integrating_docker.git' 
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t tejajenkins2 .' 
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    bat 'docker run -d --name cont12 -p 8012:80 tejajenkins2'
                }
            }
        }
        stage('Deploy Image') {
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
