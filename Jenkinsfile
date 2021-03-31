pipeline {
  agent {
    node {
      label '!windows'
    }

  }
  stages {
    stage('Build') {
      steps {
        withAnt(installation: 'ant') {
          sh 'ant compile'
        }

      }
    }

    stage('Test') {
      steps {
        withAnt(installation: 'ant') {
          sh 'ant test'
        }

      }
    }

    stage('Deploy') {
      when {
        tag 'MHA-2018-Red-Team-release-*'
      }
      steps {
        echo 'Deploying because this commit is tagged...'
        withAnt(installation: 'ant') {
          sh 'ant deploy'
        }

      }
    }

  }
  post {
    always {
      junit '**/*.xml'
    }

  }
}