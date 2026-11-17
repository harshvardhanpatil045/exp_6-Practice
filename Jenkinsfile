pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Web Application...'
                bat 'dir'
                echo 'Build completed successfully!'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Web Application...'
                bat '''
                    if not exist index.html exit /b 1
                    if not exist style.css exit /b 1
                    if not exist script.js exit /b 1
                    echo All required files are present!
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Web Application...'
                bat '''
                    if not exist "C:\\JenkinsDeploy" mkdir "C:\\JenkinsDeploy"
                    copy /Y index.html "C:\\JenkinsDeploy\\"
                    copy /Y style.css "C:\\JenkinsDeploy\\"
                    copy /Y script.js "C:\\JenkinsDeploy\\"
                '''
                echo 'Deployment completed!'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }
    }
}
