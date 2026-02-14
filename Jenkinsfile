pipeline {
    agent any

    environment {
        VENV_DIR = "venv"
        PYTHON = "venv\\Scripts\\python.exe"
    }

    stages {

        stage('Setup Python Environment') {
            steps {
                bat 'python -m venv %VENV_DIR%'
                bat '%PYTHON% -m pip install --upgrade pip'
                bat '%PYTHON% -m pip install -r requirements.txt'
            }
        }

        stage('Run Health Check') {
            steps {
                bat '%PYTHON% HealthCheck01.py'
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
