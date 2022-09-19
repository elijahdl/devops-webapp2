pipeline {
  agent {
    node {
      label 'scoob'
    }

  }
  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/elijahdl/devops-webapp2', branch: 'master')
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh '''whoami
date





echo $PATH
pwd
ls -la
./gradlew build --info'''
          }
        }

        stage('P1') {
          steps {
            sh '''date
echo run parallel'''
          }
        }

        stage('P2') {
          steps {
            sh '''date
echo more parallel lol'''
          }
        }

      }
    }

    stage('Publish') {
      steps {
        archiveArtifacts(artifacts: 'build/libs/*.war', fingerprint: true, onlyIfSuccessful: true)
      }
    }

  }
}