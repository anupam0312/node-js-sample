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
            // Stop and remove the container if it exists
            sh 'docker rm -f node-app || true'

            // Free up port 3000 (only for Docker use)
            sh '''
                used=$(docker ps --filter "publish=3000" -q)
                if [ -n "$used" ]; then
                  docker rm -f $used
                fi
            '''

            // Run the new container
            sh 'docker run -d -p 3000:3000 --name node-app node-app'
                }
            }
        }
    }
}

