pipeline {
    agent any

    environment {
        APP_NAME = "MyApp"
        VENV_DIR = "venv"
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
                bat '%VENV_DIR%\\Scripts\\activate && pip install --upgrade pip'
                bat '%VENV_DIR%\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run Health Check / Test') {
            steps {
                bat '%VENV_DIR%\\Scripts\\activate && python HealthCheck01.py'
            }
        }

        stage('Deploy Application') {
            steps {
                bat '''
                echo Deploying Application...
                start cmd /c "%VENV_DIR%\\Scripts\\activate && python HealthCheck01.py"
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
