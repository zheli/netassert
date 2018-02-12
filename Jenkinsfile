pipeline {
//  agent none // also forces each stage section contain its own agent section
  agent any

  environment {
    GIT_CREDENTIALS = "ssh-key-jenkins-bot"
  }

  stages {
    stage('Test') {
//      agent { dockerfile true }
      environment {
        PERSIST_CLUSTER = 1
        HOME="/tmp/home/"
        TEST_FILE="test/test-localhost-remote.yaml"
      }
      steps {
        ansiColor('xterm') {
          sh "command -v make &>/dev/null || yum install -yt make || apt install -y make"
          sh "make jenkins TEST_FILE=${TEST_FILE}"
        }
      }
    }
  }
}
