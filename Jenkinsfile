pipeline {
  agent none
  stages {
    stage('error') {
      steps {
        echo 'Start Test'
        sh 'whoami'
      }
    }
    stage('Maven Build') {
      steps {
        sh 'mvn build'
      }
    }
  }
}