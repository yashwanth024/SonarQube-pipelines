node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
    git credentialsId: 'Github-ID', url: 'https://github.com/pattaabhi/java-apps.git'
   }
   stage('Build') {
     withMaven(jdk: 'JDK-1.8.151', maven: 'Maven-3.5.3') {
       sh 'mvn clean compile'
     }
   }
   stage('Unit Test') {
     withMaven(jdk: 'JDK-1.8.151', maven: 'Maven-3.5.3') {
       sh 'mvn test'
     }
   }
   stage('SonarQube Analysis') {
      withSonarQubeEnv("SonarQube") {
         sh 'mvn clean install'
         sh 'mvn sonar:sonar'
       }
     }
    stage('Archival') {
      withMaven(jdk: 'JDK-1.8.151', maven: 'Maven-3.5.3') {
       sh 'mvn package'
     }
   }
     stage('Deploy to Artifactory Repo') {
     }

   
    stage('Deploy to Dev') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }
   stage('Smoke Test Execution') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }

    
   stage('Smoke Test Execution') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
    }

}
