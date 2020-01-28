pipeline {
  agent any
  options {
        timeout(time: 2, unit: 'HOURS')
        ansiColor('xterm')
  }
  stages {
      stage('Jenkins Hook') {
          steps {
            sh "echo 'HELLO THERE'"
          }
  }
  post{
    cleanup{
      deleteDir()
    }
  }
}
