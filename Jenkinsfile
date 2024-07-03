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
        stage('docker login') {
            steps {
                script {
                   withCredentials([usernamePassword(credentialsId: 'Docker', passwordVariable: 'password', usernameVariable: 'username')]) {
                    bat '''
                       echo %password% | docker login -u %username% --password-stdin
                    '''
                    }
                }
                   
                   }
                
               
            }
        }
        
        
       
        
        
    }

        
        
            
        
        
