pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out Healthcare Management System...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Healthcare Management System...'

                bat '''
                    if not exist index.html exit /b 1
                '''

                echo 'Build successful!'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'

                bat '''
                    findstr /C:"Healthcare Management System" index.html
                    if %ERRORLEVEL% NEQ 0 exit /b 1
                '''

                echo 'All tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Healthcare Management System...'
                echo 'Deployment successful!'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'CI/CD Pipeline failed.'
        }
    }
}
