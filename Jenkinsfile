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
                // This step should not normally be used in your script. Consult the inline help for details.
                   withDockerRegistry(credentialsId: 'Docker', url: 'https://hub.docker.com/repositories/tejaswimedisetti') {
                    }
                   bat "docker build -t tejaswi ."
                   }
                
               
            }
        }
        
        
       
        
        
    }

        
        
            
        
        
