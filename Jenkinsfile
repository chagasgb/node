pipeline {
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("chagasgb/node:${env.BUILD_ID}", '-f ./Dockerfile .') 
                }                
            }
        }
    }
}