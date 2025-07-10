pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/anupam0312/node-js-sample.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t node-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop and remove any running container named node-app
                    sh 'docker rm -f node-app || true'

                    // Run new container
                    sh 'docker run -d -p 3000:3000 --name node-app node-app'
                }
            }
        }
    }
}

