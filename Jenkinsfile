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
    sh "./mvnw spring-boot:build-image"
    archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
  }
  stage('Run'){
    sh "sudo docker run -d --name spring-petclinic -p 8081:8080 docker.io/library/spring-petclinic:3.1.0-SNAPSHOT"
  }
}