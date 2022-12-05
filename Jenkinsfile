pipeline {
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    dockerapp = docker.build("chagasgb/node-app:${env.BUILD_ID}", '-f ./Dockerfile .') 
                }                
            }
        }

        stage ('Push Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

        stage('Docker run') {
            steps {
                sh 'echo "PRIMEIRO ECOOOOOO"'
                sh '''
                    docker run -d -p 44:8080 --name potocoteste chagasgb/node-app:11"
                    ls -lah
                '''
            } 
        }
    }
}