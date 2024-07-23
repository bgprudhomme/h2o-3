pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'make -f scripts/Makefile.jenkins build'
            }
        }
        stage('Test') {
            steps {
                sh 'make -f scripts/Makefile.jenkins test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'make -f scripts/Makefile.jenkins deploy'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
