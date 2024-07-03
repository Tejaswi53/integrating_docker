pipeline {
    agent any  
    stages {
         stage('Checkout Code') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/Tejaswi53/integrating_docker.git' 
            }
        }
        stage('image build') {
            steps {
                bat "docker build -t tejaswi ."
            }
        }
        stage('container') {
            steps {
                bat "docker run -d --name cont19 -p 8019:80 tejaswi"
            }
        }
        
        stage('docker login') {
            steps {
                script {
                   withCredentials([usernamePassword(credentialsId: 'Docker', passwordVariable: 'password', usernameVariable: 'username')]) {
                    bat '''
                       echo %password% | docker login -u %username% -p %password%
                    '''
                    }
                }
                   }   
            }
        
        }   
    }

        
        
            
        
        
