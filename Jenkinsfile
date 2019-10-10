node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/rtimmerman/jaxlondon.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      withEnv(["MVN_HOME=$mvnHome"]) {
        sh '"$MVN_HOME/bin/mvn" clean install -Pci'
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
   }
}
