pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'my-node-app'
        DOCKER_TAG = 'latest'
        GITHUB_REPO = 'https://github.com/git-hub-sachin/hello-nodeapp.git'
    }
    
    stages {
        stage('Checkout Code') {
            steps {
                git url: "${GITHUB_REPO}"
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG) .'
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 80:80 --name ${DOCKER_IMAGE} ${DOCKER_IMAGE}:${DOCKER_TAG}'
                }
            }
        }
        
        stage('Post-Deployment') {
            steps {
                echo 'Node.js app is deployed and running on the server.'
            }
        }
    }
        
    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
