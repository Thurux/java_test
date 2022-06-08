pipeline {
  agent any
  stages {
    stage('appli_spark') {
      parallel {
        stage('test') {
          environment {
            var1 = '"bonjour"'
          }
          steps {
            echo 'hello face de test !'
            git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
            sh 'mvn clean install'
          }
        }

        stage('appli_junit') {
          steps {
            git(url: 'https://github.com/Thurux/java_test.git', branch: 'master')
            sh 'mvn clean install'
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
        sh 'echo "Fin des taches, c\'est tout OK !!"'
      }
    }

  }
}