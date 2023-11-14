node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
  stage('Build'){
    sh "echo 'admin' | sudo -S ./mvnw spring-boot:build-image;"
    archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
  }
}