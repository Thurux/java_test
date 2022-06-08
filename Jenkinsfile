pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh 'mvn clean test'
        junit 'target/surefire-reports/*.xml'
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('build') {
      steps {
        git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
        sh 'mvn clean install'
      }
    }

    stage('end') {
      steps {
        sh 'echo "Alles Gut"'
      }
    }

  }
}