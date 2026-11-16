
pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading project from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the web application...'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing project files...'
                bat 'if not exist index.html exit /b 1'
                bat 'if not exist style.css exit /b 1'
                bat 'if not exist script.js exit /b 1'
                bat 'findstr /C:"style.css" index.html >nul'
                bat 'findstr /C:"script.js" index.html >nul'
                echo 'All tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'
                bat 'if not exist "C:\\Jenkins-CICD-Deploy" mkdir "C:\\Jenkins-CICD-Deploy"'
                bat 'copy /Y index.html "C:\\Jenkins-CICD-Deploy\\"'
                bat 'copy /Y style.css "C:\\Jenkins-CICD-Deploy\\"'
                bat 'copy /Y script.js "C:\\Jenkins-CICD-Deploy\\"'
                echo 'Deployment completed!'
            }
        }
    }
}
