pipeline {
    agent any

    tools {
        // Install the maven version configured as "mvn" and add it to the path.
        maven "mvn"
    }

    stages {
        stage('Test') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/SuryaChaitanyaReddy/java-hello-world-with-maven-1'
                sh "mvn clean package"1.git
            }
        }
        stage('dockerbuild') {
            steps {
                sh "docker build . -t suryachaitanyareddy/javahello:${BUILD_NUMBER}"
            }
        }
        stage('dockerpush') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerregistry') {
                        sh "docker push suryachaitanyareddy/javahello:${BUILD_NUMBER}"
                    }
                }      
            }    
        }    
    }
}
