pipeline {
  agent {
    docker {
      image 'maven:3.5.0-jdk-8'
    }
    
  }
  stages {
    stage('Stage msg') {
      steps {
        echo 'Start Test'
        sh 'mvn test'
      }
    }
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
    stage('Test case') {
      steps {
        parallel(
          "Archiving": {
            archiveArtifacts(onlyIfSuccessful: true, artifacts: 'target/**/*.jar')
            
          },
          "Install": {
            sh 'sudo apt-get update && sudo apt-get install junit'
            
          }
        )
      }
    }
    stage('Test cases') {
      steps {
        junit ' junit target/surefire-reports/*.xml'
      }
    }
  }
}