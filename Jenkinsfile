pipeline {
    agent {
        docker {
            image 'ubuntu:20.04'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
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
