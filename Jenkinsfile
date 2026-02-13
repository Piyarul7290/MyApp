pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/Piyarul7290/MyApp', branch: 'main')
      }
    }

    stage('Log') {
      steps {
        sh '''la -ls
'''
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile.'
      }
    }

  }
}