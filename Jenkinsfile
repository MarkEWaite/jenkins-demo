pipeline {
    agent {
        label '!windows'
    }
    stages {
        stage('Build') {
            steps {
                sh 'ant compile'
            }
        }
        stage('Test') {
            steps {
                sh 'ant test'
            }
        }
        stage('Deploy') {
            when { tag "MHA-2018-Red-Team-release-*" }
            steps {
                echo 'Deploying because this commit is tagged...'
                sh 'ant deploy'
            }
        }
    }
    post {
        always {
            junit '**/*.xml'
        }
    }
}
