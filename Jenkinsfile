pipeline {
  agent any
  stages {
    stage('Parallel execution') {
      parallel {
        stage('Hello world') {
          steps {
            sh 'echo "hello world"'
          }
        }

        stage('hello world1') {
          steps {
            sh 'echo "hello world2"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
          }
        }

      }
    }

  }
}