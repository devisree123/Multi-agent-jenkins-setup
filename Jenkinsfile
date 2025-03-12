pipeline {
    agent none
    stages {
        stage('Back-end') {
            agent {
                docker {
                    image 'maven:3.8.1-adoptopenjdk-11'
                    // Convert Windows path to Unix-style directly in the Docker args
                    args "--user root -w $(cygpath -u \"$WORKSPACE\")"
                }
            }
            steps {
                sh '''
                    echo "Running Maven build in $WORKSPACE"
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
