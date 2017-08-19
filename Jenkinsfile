pipeline {
  agent {
    docker {
      image 'maven:3.5.0-jdk-8'
    }
    
  }
  stages {
    stage('Stage msg') {
      steps {
        parallel(
          "Stage msg": {
            echo 'Start Test'
            sh 'mvn test'
            
          },
          "Maven Test": {
            echo 'MAVEN TEST'
            
          }
        )
      }
    }
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }
    stage('Archiving') {
      steps {
        parallel(
          "Archiving": {
            archiveArtifacts(onlyIfSuccessful: true, artifacts: 'target/**/*.jar')
            
          },
          "Archiving Jar": {
            echo 'archiving jar'
            
          }
        )
      }
    }
    stage('Test cases') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }
    stage('') {
      steps {
        tool(name: 'maven', type: 'apache-maven-3.0.1')
      }
    }
  }
}