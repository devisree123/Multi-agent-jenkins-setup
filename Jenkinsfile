pipeline {
    agent none
    
    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                script {
                    // Create a simple Java Hello World application
                    writeFile file: 'HelloWorld.java', text: '''
                    public class HelloWorld {
                        public static void main(String[] args) {
                            System.out.println("Hello, World from Java!");
                        }
                    }
                    '''
                    
                    // Compile and run Java app
                    sh 'javac HelloWorld.java'
                    sh 'java HelloWorld'
                }
            }
        }
        
        stage('Front-end') {
            agent {
                docker { image 'node:16-alpine' }
            }
            steps {
                script {
                    // Create a simple Node.js Hello World application
                    writeFile file: 'app.js', text: '''
                    console.log("Hello, World from Node.js!");
                    '''
                    
                    // Execute Node.js app
                    sh 'node app.js'
                }
            }
        }
    }
}
