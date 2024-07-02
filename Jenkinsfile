pipeline {
    agent any  
    environment {
        DOCKER_HUB_USERNAME = credentials('Docker') 
        DOCKER_HUB_PASSWORD = credentials('Docker')
    }
     
    stages {
         stage('Checkout Code') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/Tejaswi53/integrating_docker.git' 
            }
        }
        
        stage('Docker login') {
            steps {
                bat "echo ${DOCKER_HUB_USERNAME}"
                bat "docker login -u tejaswimedisetti -p shashiteja@3028"
            }
        }
        stage('image build') {
            steps {
                bat "docker build -t tejaswi ."
            }
        }
        stage('container') {
            steps {
                bat "docker run -d --name cont15 -p 8015:80 tejaswi"
            }
        }
        
    }
}
        
        
            
        
        
