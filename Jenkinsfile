node {
   def mvnHome
   
   stage('Build') {
      // Run the maven build
         sh "'${mvnHome}/bin/mvn'  -Dmaven.failure.ignore clean"
         sh "'${mvnHome}/bin/mvn' -Dmaven.failure.ignore package"
   }
   stage('Test'){
       sh "'${mvnHome}/bin/mvn' -Dmaven.failure.ignore test"
       sh "'${mvnHome}/bin/mvn' -Dmaven.failure.ignore test checkstyle:checkstyle"
       
   }
   
   
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
