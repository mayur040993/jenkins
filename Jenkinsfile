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
        parallel(
          "build": {
            sh 'mvn package'
            
          },
          "archive": {
            sh 'archive "target/**/*.jar"'
            
          }
        )
      }
    }
    stage('Test case') {
      steps {
        sh '''
junit target/surefire-reports/*.xml'''
      }
    }
  }
}