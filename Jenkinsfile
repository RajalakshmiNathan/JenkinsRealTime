pipeline {
  agent any
  stages {
    stage('Dev-Build-Deploy') {
      steps {
        git(url: 'https://github.com/RajalakshmiNathan/WebApp', branch: 'main', poll: true)
      }
    }

  }
}