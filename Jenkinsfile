pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker {
                    image 'maven:3.8.1-adoptopenjdk-11'
                    args '--user root'
                }
            }
            environment {
                WORKSPACE_UNIX = sh(script: 'cygpath -u "$WORKSPACE"', returnStdout: true).trim()
            }
            steps {
                sh '''
                    echo "Running Maven build in $WORKSPACE_UNIX"
                    cd $WORKSPACE_UNIX
                    mvn clean install
                '''
            }
        }
        stage('Front-end') {
            agent none
            steps {
                echo 'Skipping front-end build for now...'
            }
        }
    }
}
