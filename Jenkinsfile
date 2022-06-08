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
            sh 'git clone https://github.com/kliakos/sparkjava-war-example.git'
            sh 'mvn clean install'
          }
        }

        stage('appli_junit') {
          steps {
            sh 'git clone https://github.com/Thurux/java_test.git'
            sh 'mvn clean install'
          }
        }

      }
    }

    stage('junit-reports') {
      steps {
        junit '/appli_junit/target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo "Fin des tâches, c\'est tout OK !!"'
      }
    }

  }
}