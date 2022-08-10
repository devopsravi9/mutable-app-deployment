pipeline {
  agent any

  options {
    ansiColor('xterm')
  }

  parameters {
    choice(name: 'ENV', choices: ['', 'dev', 'prod'], description: '')
    choice(name: 'COMPONENT', choices: ['shipping'], description: '')
  }

  stages {
    stage('terraform') {
      steps {
        sh '''
          terraform init
//          terraform apply -auto-approve -var ENV=${ENV} -var COMPONENT=${COMPONENT} parallelism=1
          terraform apply -auto-approve -var ENV=${ENV} -var COMPONENT=${COMPONENT}
        '''
        }
      }
    }
  post {
    always {
      cleanWs ()
      }
    }
  }

// parallelism = 1 or all, to deploy content to  all instances of one component at a time or one after one.