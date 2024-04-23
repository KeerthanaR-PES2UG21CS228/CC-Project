pipeline {
    agent {
        docker { 
            image 'node:14-alpine' 
            args '-v $PWD:/app -w /app'
        }
    }

    stages {
        stage('Install Node.js dependencies') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Build and Run Backend') {
            steps {
                dir('backend') {
                    sh 'npm start &'
                }
            }
        }

        stage('Build and Run Frontend') {
            steps {
                dir('frontend/e-commerce') {
                    sh 'npm start &'
                }
            }
        }
    }
}
