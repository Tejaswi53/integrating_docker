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
                bat "docker login -u ${DOCKER_HUB_USERNAME} -p ${DOCKER_HUB_PASSWORD}"
            }
        }
    }
}
        
        
            
        
        
