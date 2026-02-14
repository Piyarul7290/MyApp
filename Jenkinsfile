pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Piyarul7290/MyApp.git'
            }
        }

        stage('Log') {
            steps {
                bat 'echo Pipeline Started'
            }
        }

        stage('Build') {
            steps {
                bat 'python --version'
                bat 'echo Build Successful'
            }
        }
    }
}
