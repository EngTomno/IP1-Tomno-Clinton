pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                echo 'Cloning repository...'
                git url: 'https://github.com/EngTomno/IP1-Tomno-Clinton.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'make build'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'make test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to Heroku...'
                sh 'git push https://git.heroku.com/gallerydevops.git HEAD:master'
            }
        }
    }
    post {
        success {
            slackSend color: 'good', message: "Deployment to Heroku successful."
        }
        failure {
            slackSend color: 'danger', message: "Deployment to Heroku failed."
        }
    }
}
