node("maven-label") {
   def mvnHome
   stage('Preparation') { https://github.com/qf-master-card/master-card.git
      
      git 'https://github.com/qf-master-card/master-card.git'
                
      mvnHome = tool 'maven'
   }
   stage('Build') {
    
      withEnv(["MVN_HOME=$mvnHome"]) {
         if (isUnix()) {
            sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
         } else {
            bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         }
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
}
