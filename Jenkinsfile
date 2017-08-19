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
        sh 'archive "target/**/*.jar"'
        archiveArtifacts(onlyIfSuccessful: true, artifacts: 'target/**/*.jar')
      }
    }
  }
}