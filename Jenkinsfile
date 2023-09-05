pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Use the 'checkout' step to fetch the code from the Git repository
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/dhakersghaier/1st']]])
            }
        }

        stage('Build and Test') {
            steps {
                // Use the 'node' block to allocate a build agent for this stage
                node('any') {
                    // Inside the 'node' block, you can run build and test steps
                    sh 'npm install'
                    sh 'npm test'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Another 'node' block for deployment, if needed
                node('any') {
                    // Deployment steps
                    // For example, you can use a tool like PM2 to run your Node.js app
                    sh 'npm install -g pm2'
                    sh 'pm2 start app.js'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
