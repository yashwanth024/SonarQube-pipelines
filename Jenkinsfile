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
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
         withMaven(jdk: 'JDK-1.8.151', maven: 'Maven-3.5.3') {
           sh ' mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package org.sonarsource.scanner.maven:sonar-maven-plugin:3.4.0.905:sonar -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=pattabhi -Dsonar.login=pattabhi -Dsonar.password=df5bb81bae9ba310d6a38135b957227ba6ecd32c '
 
         //sh 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package org.sonarsource.scanner.maven:sonar-maven-plugin:3.4.0.905:sonar ' +
            //' -Dsonar.host.url=https://sonarcloud.io '+
            //' -Dsonar.organization=pattabhi '+
            //' -Dsonar.projectKey=Pattabhi:com.pattabhi ' +
            //' -Dsonar.login=pattabhi ' 
            //' -Dsonar.password=df5bb81bae9ba310d6a38135b957227ba6ecd32c ' 
            
            
            //clean org.jacoco:jacoco-maven-plugin:prepare-agent package org.sonarsource.scanner.maven:sonar-maven-plugin:3.4.0.905:sonar 
            //-Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=xxxx-github -Dsonar.login=yyyy
        }
      //}
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
