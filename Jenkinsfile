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

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh './ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
            skipDefaultCheckout(true)
          }
        }

        stage('clone down') {
   
          steps {
            stash name: 'code', excludes: '.git'
            unstash name: 'code'
          }
        }

      }
    }

  }
}