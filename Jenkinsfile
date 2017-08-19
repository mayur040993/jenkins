pipeline {
  agent {
    docker {
      image 'maven:3.5.0-jdk-8'
    }
    
  }
  stages {
    stage('') {
      steps {
        parallel(
          "Start test": {
            echo 'Start Test'
            
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