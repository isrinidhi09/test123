pipeline{
  agent any
  environment{
    PYTHON_PATH='C:\Users\srini\AppData\Local\Programs\Python\Python312;C:\Users\srini\AppData\Local\Programs\Python\Python312\scripts'
  }
  stage{
    stage('checkout'){
      steps{
        checkout scm
      }
    }
  }
  stage('build'){
        steps{
          bat '''
          set PATH=%PYTHON-PATH%,%PATH%
          pip install -r requirement.txt
          '''
}
      }
        stage('Sonarqube-Analysis'){
          environment{
            SONAR-TOKEN=credentials('sonar-token')
          }
          step{
            bat '''
             set PATH=%PYTHON-PATH%,%PATH%
            
           }
}


  
