pipeline {
  agent {
    node {
      label 'slave1'
    }

  }
  stages {
    stage('SourceCode') {
      steps {
        git(url: 'https://github.com/MKBN/mbn-spring-boot-project02.git', branch: 'master', poll: true)
      }
    }

    stage('compile') {
      parallel {
        stage('compile') {
          steps {
            sh 'mvn compile'
          }
        }

        stage('Message') {
          steps {
            echo 'Compiling the Code '
          }
        }

      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('package') {
      steps {
        sh 'mvn package'
      }
    }

    stage('End') {
      steps {
        echo 'End of the Project'
      }
    }

  }
}