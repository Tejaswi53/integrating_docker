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
        stage {
            steps {
                // This step should not normally be used in your script. Consult the inline help for details.
withDockerRegistry(credentialsId: 'Docker') {
    // some block
}
            }
        }
        
       
        stage('image build') {
            steps {
                bat "docker build -t tejaswi ."
            }
        }
        stage('container') {
            steps {
                bat "docker run -d --name cont18 -p 8018:80 tejaswi"
            }
        }
        stage('pushing image to docker') {
            steps {
                bat "docker tag tejaswi tejaswimedisetti/tejaswim"
                bat "docker push tejaswimedisetti/tejaswim"
            }
        }
        
    }
}
        
        
            
        
        
