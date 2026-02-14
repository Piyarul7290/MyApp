pipeline {
    agent any

    environment {
        APP_NAME = "MyApp"
        VENV_DIR = "venv"
        PYTHON = "venv\\Scripts\\python.exe"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Piyarul7290/MyApp.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                bat 'python -m venv %VENV_DIR%'
                bat '%PYTHON% -m pip install --upgrade pip'
                bat '%PYTHON% -m pip install -r requirements.txt'
            }
        }

        stage('Run Health Check / Test') {
            steps {
                bat '%PYTHON% HealthCheck01.py'
            }
        }

        stage('Deploy Application') {
            steps {
                bat '''
                echo Deploying Application...
                start "" %PYTHON% HealthCheck01.py
                '''
            }
        }
    }

    post {
        success {
            bat 'echo CI/CD Pipeline Completed Successfully!'
        }
        failure {
            bat 'echo Pipeline Failed!'
        }
    }
}
