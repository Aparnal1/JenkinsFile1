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
      when
          {
            branch 'master'
          }
      parallel {
        
        stage('Deploy') {
          
          steps {
            input 'Do you want proceed?'
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
