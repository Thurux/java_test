pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test') {
          environment {
            var1 = '"bonjour"'
          }
          steps {
            echo 'hello face de test !'
            sh 'mvn clean test'
          }
        }

        stage('Build/Git/sparkjava') {
          steps {
            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
            sh 'mvn clean install'
            archiveArtifacts 'target/.war'
          }
        }

      }
    }

    stage('junit-reports') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo "Fin des tâches, c\'est tout OK !!"'
      }
    }

  }
}