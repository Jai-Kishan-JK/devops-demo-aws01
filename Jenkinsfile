pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Jenkins automatically pulls the code from GitHub
                echo 'Pulling latest code from GitHub...'
            }
        }
        stage('Test') {
            steps {
                // A dummy test step (e.g., checking if index.html exists)
                echo 'Testing code structure...'
                sh 'test -f index.html'
            }
        }
        stage('Deploy to AWS App Server') {
            steps {
                echo 'Deploying application to Production EC2...'
                // Jenkins securely copies the file to your App Server using SSH
                sshagent(['aws-app-server-key']) {
                    sh 'scp -o StrictHostKeyChecking=no index.html ubuntu@54.196.128.153:/var/www/html/'
                }
            }
        }
    }
}
