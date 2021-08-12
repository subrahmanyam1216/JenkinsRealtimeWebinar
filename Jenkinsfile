pipeline {
     agent any
     tools { 
      maven 'M2_HOME' 
      jdk 'JAVA_HOME' 
    }
     stages {
       stage('Pullcode') {
         steps {
             git 'https://github.com/cbabu85/Webinar.git'
         }
       }
       stage('Testing') {
          steps {
            sh 'mvn clean test'
            junit 'target/surefire-reports/*.xml'
          }
        }
        //stage('Code coverage') {
        //  steps {
        //     sh 'mvn cobertura:cobertura'
        //     cobertura autoUpdateHealth: false, autoUpdateStability: false, coberturaReportFile: '**/target/site/cobertura/coverage.xml', failUnhealthy: false, failUnstable: false
       //   }
       // }
        stage('Package') {
          steps { 
            sh 'mvn package -DskipTests=true'
          }
        }
      }
      post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
      }
}
