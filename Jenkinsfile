pipeline {
    agent any

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
    }
}
