node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
    git credentialsId: 'Github-ID', url: 'https://github.com/InfinityVegas/wannacry.git'
   }
   stage('Build') {
     withMaven( maven: 'LOCALMAVEN') {
       sh 'mvn clean compile'
     }
   }
   stage('Unit Test') {
     withMaven(maven: 'LOCALMAVEN') {
       sh 'mvn test'
     }
   }
   stage('SonarQube Analysis') {
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
      //}
      withMaven( maven: 'LOCALMAVEN')
          sh ' mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=pattabhi '+ 
             ' -Dsonar.login=df5bb81bae9ba310d6a38135b957227ba6ecd32c '
          }
      }
   
    //stage("Quality Gate"){
          //timeout(time: 1, unit: 'HOURS') {
             // def qg = waitForQualityGate()
              //if (qg.status != 'OK') {
                //  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              //}
         // }
     // }
   
    stage('Archival') {
      withMaven( maven: 'LOCALMAVEN')
       //sh 'mvn package'
     }
   
     stage('Deploy to Artifactory Repo') {
     }

   
    stage('Deploy to Dev') {
      
   }
   stage('Smoke Test Execution') {
      
   }

    

