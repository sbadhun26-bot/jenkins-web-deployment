
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub'
                checkout scm
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to Apache'

                sh '''
                    cp "$WORKSPACE/index.html" /var/www/html/index.html
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    ls -l /var/www/html/index.html
                    echo "Deployment verification completed"
                '''
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
