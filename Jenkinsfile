pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Use the 'checkout' step to fetch the code from the Git repository
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/dhakersghaier/1st']]])
            }
        }
        stage('Install Dependencies') {
           steps {
               script {
                 // Change to the directory where package.json is located
                   dir('1st/package.json') {
                // Install project dependencies locally
                    sh 'npm ci'
                       }
         }
    }
}

        stage('Build and Test') {
            steps {
        
                    // Inside the 'node' block, you can run build and test steps
                    sh 'npm install'
                    sh 'npm --version'
                }
            }
        

        stage('Deploy') {
            steps {
                    // Deployment steps
                    // For example, you can use a tool like PM2 to run your Node.js app
                    sh 'npm install pm2'
                    sh './node_modules/pm2/bin/pm2 start server.js'
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
