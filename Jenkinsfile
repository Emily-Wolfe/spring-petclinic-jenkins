pipeline {
  agent any
  stages {
    stage('Static Analysis') {
      steps {
        withSonarQubeEnv 'SonarQube'
      }
    }

  }
}