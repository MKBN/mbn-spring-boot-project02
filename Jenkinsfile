pipeline {
  agent {
    node {
      label 'slave1'
    }

  }
  stages {
    stage('SourceCode') {
      parallel {
        stage('SourceCode') {
          steps {
            git(url: 'https://github.com/MKBN/mbn-spring-boot-project02.git', branch: 'master', poll: true)
          }
        }

        stage('Maven') {
          steps {
            tool(name: 'Maven', type: 'slave1')
          }
        }

      }
    }

    stage('compile') {
      steps {
        sh 'mvn compile'
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