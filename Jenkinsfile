pipeline {
    agent any

    environment {
        IMAGE_NAME = 'joeljxhnson/web-app'
        IMAGE_TAG  = 'latest'
    }

    stages {
        stage('Git Clone') {
            steps {
                git branch: 'main', changelog: false, poll: true, url: 'https://github.com/jojohnoson/App_Deployment_CI-CD.git'
            }
        }
        stage('Listing the files'){
            steps{
                sh 'ls'
            }
        }
        stage('Docker build'){
            steps{
                sh "docker build -t $IMAGE_NAME:$IMAGE_TAG ."

            }
        }
        stage('Docker push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials-id', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                        
                        // Jenkins logs in
                        sh "echo \$DOCKER_PASS | docker login -u \$DOCKER_USER --password-stdin"
                        
                        // Jenkins pushes the image
                        sh "docker push ${IMAGE_NAME}:${IMAGE_TAG}"
                    }
            }
        }
    }
}
