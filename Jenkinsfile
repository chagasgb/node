pipeline {
    agent any


    stages {
        stage ('Build Image') {
            steps {
                script {
                if (env.BRANCH_NAME == 'dev') {
                    dockerapp = docker.build("chagasgb/node-app-dev:${env.BUILD_ID}", '-f ./Dockerfile .')
                } else if (env.BRANCH_NAME == 'main') {
                    dockerapp = docker.build("chagasgb/node-app:${env.BUILD_ID}", '-f ./Dockerfile .')
                }

            }                
        }
    }

        stage ('Push Image') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'master') {
                        echo 'FOI NA MAAAAAAAAAASTER'
                    //    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                    //    dockerapp.push("${env.BUILD_ID}")
                    } else {
                        echo 'NAO FOI NA MASTEEEEEER'
                    }
                }
            }
        }

        stage("Deploy to User test") {
            steps {
                sh 'docker run -d -p 44:8080 --name node-app-dev-$BUILD_NUMBER chagasgb/node-app:$BUILD_NUMBER'
            }
        }
    }
}