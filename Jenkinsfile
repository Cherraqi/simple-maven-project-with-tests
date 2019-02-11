node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/Cherraqi/simple-maven-project-with-tests'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
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
