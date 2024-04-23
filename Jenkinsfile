pipeline {
    agent any
    
    environment {
        // Define the Node.js version you want to use
        NODEJS_VERSION = '14'
    }
    
    stages {
        stage('Install Node.js') {
            steps {
                // Install Node.js using nvm (Node Version Manager)
                script {
                    sh '''
                    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    nvm install ${NODEJS_VERSION}
                    nvm use ${NODEJS_VERSION}
                    npm config delete prefix
                    npm install -g npm@latest
                    '''
                }
            }
        }
        stage('Build') {
            steps {
                // Navigate to the backend directory and install backend dependencies
                dir('backend') {
                    sh 'npm install'
                }
                
                // Navigate to the frontend/e-commerce directory and start the frontend server
                dir('frontend/e-commerce') {
                    sh 'npm install'
                    sh 'npm start &'
                }
            }
        }
    }
}
