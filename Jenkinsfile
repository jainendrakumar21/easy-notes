pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "my_maven"
   }
   
   

   stages {
        stage('SCM') {
            steps {
            // Get some code from a GitHub repository
                git url: 'https://github.com/narendrajava1/easy-notes.git'
            }
        }
      stage('build') {
         steps {
            
            // Run Maven on a Unix agent.
            sh "mvn -Dmaven.test.failure.ignore=true clean install sonar:sonar"

         }
     }
         
      stage('Sonarqube') {
      
          environment {
              scannerHome = tool 'LocalSonarQubeScanner'
          }
          steps {
              withSonarQubeEnv('localscanner') {
              sh "${scannerHome}/bin/sonar-scanner"
              }
        // 	  timeout(time: 10, unit: 'MINUTES') {
        //       waitForQualityGate abortPipeline: true
        //       }
          }
       

          post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
            success {
               junit '**/target/surefire-reports/TEST-*.xml'
               archiveArtifacts 'target/*.jar'
            }
         }
      }
   }
}
