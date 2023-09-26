pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
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
                // Deployment commands
                sh 'gunicorn -c config/gunicorn/dev.py'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
