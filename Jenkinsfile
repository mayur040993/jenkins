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
        sh 'mvn build'
      }
    }
  }
}