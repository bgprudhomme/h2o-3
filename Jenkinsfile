pipeline {
    agent {
        docker {
            image 'ubuntu:20.04'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Install Docker') {
            steps {
                sh '''
                apt-get update
                apt-get install -y docker.io
                '''
            }
        }
        stage('Verify Docker') {
            steps {
                sh 'docker --version'
            }
        }
        stage('Install Make') {
            steps {
                sh 'apt-get update && apt-get install -y make'
            }
        }
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
}
