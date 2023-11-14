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
    sh 'sudo ./mvnw spring-boot:build-image;' 
    archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
  }
}