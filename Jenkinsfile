pipeline {
  agent any

  parameters {
    choice(name: 'ENV', choices: ['', 'dev', 'prod'], description: '')
    choice(name: 'COMPONENT', choices: ['shipping'], description: '')
  }

  stages {
    stage('terraform') {
      steps {
        sh '''
          terraform init
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