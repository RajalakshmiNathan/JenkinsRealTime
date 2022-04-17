pipeline {
  agent any
  stages {
    stage('Dev-Build-Stage') {
      steps {
        git(url: 'https://github.com/RajalakshmiNathan/WebApp.git', branch: 'main', poll: true)
        bat 'mvn install'
        bat 'StartApp.bat'
        script {
          try{
            bat 'StopApp.bat'
          }catch(Exception e){
            echo "no apps running in port 9002"
          }
        }

      }
    }

    stage('Ui Automation') {
      parallel {
        stage('Ui Automation') {
          steps {
            git 'https://github.com/RajalakshmiNathan/WebAppUiAutomation.git'
            bat 'mvn test'
          }
        }

        stage('Api Automation') {
          steps {
            git 'https://github.com/RajalakshmiNathan/WebAppApiAutomation.git'
            bat 'mvn test'
          }
        }

        stage('Performance Testing') {
          steps {
            echo 'Jmeter installation'
          }
        }

      }
    }

    stage('UAT') {
      steps {
        echo 'UAT Execution'
      }
    }

  }
  environment {
    PATH = 'C:\\Windows\\System32'
  }
}
