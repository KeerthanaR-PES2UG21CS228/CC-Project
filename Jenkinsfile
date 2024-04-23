pipeline {
    agent any
    stages {
        stage('Tests') {
            steps {
                script {
                    // Define the Docker image to use
                    def dockerImage = 'node:10-stretch'
                    
                    // Run steps inside the Docker container
                    docker.image(dockerImage).inside { 
                        echo 'Building..'
                        sh 'npm install'
                        echo 'Testing..'
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Install and Start') {
            steps {
                // Navigate to the backend directory and install backend dependencies
                dir('backend') {
                    echo 'Installing backend dependencies..'
                    sh 'npm install'
                }
                
                // Navigate to the frontend/e-commerce directory and start the frontend server
                dir('frontend/e-commerce') {
                    echo 'Installing frontend dependencies..'
                    sh 'npm install'
                    echo 'Starting frontend server..'
                    sh 'npm start &'
                }
            }
        }
    }
}
