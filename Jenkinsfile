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
    sh "echo '164bc6882390476282c4b9b73dd37df7' | sudo -S ./mvnw spring-boot:build-image;"
    archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
  }
}