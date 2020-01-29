void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "${env.GIT_URL}"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}

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
            setBuildStatus("Success", "SUCCESS")
          }
  }
}
  post{
    cleanup{
      deleteDir()
    }
  }
}
