pipeline {
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("node_app:${env.BUILD_ID}", '-f ./Dockerfile .') 
                }                
            }
        }
    }
}