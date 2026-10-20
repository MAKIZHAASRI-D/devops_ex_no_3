pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh 'test -f index.html'
                echo 'HTML file exists - Test passed'
            }
        }

        stage('Build') {
            steps {
                echo 'Preparing HTML application...'
                sh 'mkdir -p build'
                sh 'cp index.html build/'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying HTML application...'
                archiveArtifacts artifacts: 'build/index.html',
                                 fingerprint: true
                echo 'HTML application deployment stage completed!'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}