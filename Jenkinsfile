pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build step'
          }
        }

        stage('Test') {
          steps {
            echo 'Test'
            writeFile(file: 'logtest.txt', text: 'This is log file')
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            input 'DO you want proceed?'
            echo 'Deployment stage'
          }
        }

        stage('Artifact') {
          steps {
            archiveArtifacts(artifacts: 'logtest.txr', allowEmptyArchive: true)
          }
        }

      }
    }

  }
}