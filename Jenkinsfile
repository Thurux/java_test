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
            sh 'touch bonjour'
            sh 'mvn clean test'
          }
        }

        stage('Build/Git/sparkjava') {
          environment {
            JAVA_HOME = '/usr/lib/jvm/java-8-openjdk'
          }
          steps {
            sh 'git clone https://github.com/kliakos/sparkjava-war-example.git'
            sh 'cd sparkjava-war-example/'
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