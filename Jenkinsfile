pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        sh 'sh scripts/test.sh'
      }
    }

    stage('build') {
      steps {
        sh 'sh scripts/build.sh'
      }
    }

    stage('docker-build') {
      steps {
        sh 'docker build -t loensky/cicdtest'
      }
    }

    stage('docker-push') {
      steps {
        sh '''docker.withRegistry(\'https://registry.hub.docker.com\', \'docker_hub_creds_id\') {
    def app = docker.image("loensky/cicdtest")
    app.push("latest")
}
'''
        }
      }

    }
  }