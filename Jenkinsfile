pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
            }
        }

        stage('Build') {
            steps {
                echo 'Build completed successfully!'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing web application...'

                bat 'if exist index.html (echo index.html found) else (exit /b 1)'
                bat 'if exist style.css (echo style.css found) else (exit /b 1)'
                bat 'if exist script.js (echo script.js found) else (exit /b 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying web application...'

                bat 'if not exist deploy mkdir deploy'
                bat 'copy /Y index.html deploy\\'
                bat 'copy /Y style.css deploy\\'
                bat 'copy /Y script.js deploy\\'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check console output.'
        }
    }
}
