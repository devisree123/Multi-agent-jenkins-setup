pipeline {
    agent any
    environment {
        DOCKER_WORKDIR = '/workspace' // Updated to a Unix-style absolute path
    }
    stages {
        stage('Back-end') {
            agent {
                docker {
                    image 'maven:3.8.1-adoptopenjdk-11'
                    args '-v $WORKSPACE:/workspace -w /workspace'
                }
            }
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
            }
        }
        stage('Front-end') {
            agent {
                docker {
                    image 'node:14'
                    args '-v $WORKSPACE:/workspace -w /workspace'
                }
            }
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
    }
}

