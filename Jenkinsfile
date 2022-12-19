def remote = [:]
    remote.name = 'desktop-48'
    remote.host = '9.9.9.123'
    remote.user = 'desktop-48'
    remote.password = 'Test105*'
    remote.allowAnyHosts = true

pipeline {
  agent {label 'docker-agent'}
  stages {
    stage ('Build') {
      steps {
        script {
          dockerImage = docker.build "django"
        }
      }
    }
    stage ('Remote SSH') {
      steps {
        script {
          sshCommand remote: remote, command: "pwd", sudo: true
        }
      }
    }
  }
}