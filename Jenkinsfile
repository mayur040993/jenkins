pipeline {
  agent {
    docker {
      image 'maven:3.5-jdk-8'
    }
    
  }
  stages {
    stage('error') {
      steps {
        parallel(
          "Start test": {
            echo 'Start Test'
            sh 'whoami'
            
          },
          "Maven test": {
            sh 'mvn test'
            
          }
        )
      }
    }
    stage('Maven Build') {
      steps {
        sh 'mvn build'
      }
    }
  }
}