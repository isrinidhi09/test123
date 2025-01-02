pipeline {
    agent any
    environment {
        PYTHON_PATH = 'C:\\Users\\srini\\AppData\\Local\\Programs\\Python\\Python312\\;C:\\Users\\srini\\AppData\\Local\\Programs\\Python\\Python312\\Scripts\\'
    }
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('List Files') {
            steps {
                bat 'dir /s'
            }
        }
        stage('build') {
            steps {
                bat '''
                set PATH=%PYTHON_PATH%;%PATH%
                if exist requirements.txt (
                    pip install -r requirements.txt
                ) else (
                    echo requirements.txt not found. Skipping pip install.
                    exit 1
                )
                '''
            }
        }
        stage('Sonarqube-Analysis') {
            environment {
                SONAR_TOKEN = credentials('sonar-token')
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


