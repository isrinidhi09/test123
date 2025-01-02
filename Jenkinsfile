pipeline {
  agent any
  environment {
    PYTHON_PATH = 'C:\\Users\\srini\\AppData\\Local\\Programs\\Python\\Python312;C:\\Users\\srini\\AppData\\Local\\Programs\\Python\\Python312\\scripts'
  }
  stages {
    stage('checkout') {
      steps {
        checkout scm
      }
    }
    stage('build') {
      steps {
        bat '''
        set PATH=%PYTHON_PATH%;%PATH%
        pip install -r requirement.txt
        '''
      }
    }
    stage('Sonarqube-Analysis') {
      environment {
        SONAR_TOKEN = credentials('sonar-token') // Replaced SONAR-TOKEN with SONAR_TOKEN
      }
      steps {
        bat '''
        set PATH=%PYTHON_PATH%;%PATH%
        sonar-scanner -Dsonar.projectKey=demopl ^
        -Dsonar.sources=. ^
        -Dsonar.host.url=http://localhost:9000 ^
        -Dsonar.token=%SONAR_TOKEN%
        '''
      }
    }
  }
}

