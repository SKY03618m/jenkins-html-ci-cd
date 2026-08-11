pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                git branch: 'main',
                    url: 'https://github.com/SKY03618m/jenkins-html-ci-cd.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build completed successfully.'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing web files...'
                bat 'if exist index.html (echo index.html found) else (exit /b 1)'
                bat 'if exist style.css (echo style.css found) else (exit /b 1)'
                bat 'if exist script.js (echo script.js found) else (exit /b 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying files to IIS...'
                bat 'xcopy /Y /I index.html C:\\inetpub\\wwwroot\\'
                bat 'xcopy /Y /I style.css C:\\inetpub\\wwwroot\\'
                bat 'xcopy /Y /I script.js C:\\inetpub\\wwwroot\\'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
