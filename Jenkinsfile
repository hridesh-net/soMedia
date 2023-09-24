pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build commands
                sh 'source smenv/bin/activate'
                sh 'pip3 install -r requirements.txt'
                sh 'python3 manage.py collectstatic --noinput'
            }
        }

        stage('Deploy') {
            steps {
                // Replace with your deployment commands
                sh 'gunicorn -c config/gunicorn/dev.py'
            }
        }
    }

    post {
        success {
            // Notify about successful deployment, send notifications, etc.
            echo 'Deployment successful!'
        }
        failure {
            // Notify about deployment failure, send notifications, etc.
            echo 'Deployment failed!'
        }
    }
}
