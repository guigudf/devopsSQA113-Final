pipeline {
    agent any
    environment {
        FIREBASE_TOKEN = credentials('firebase-token') 
    }
    stages {
        stage('Build') {
            steps {
                echo 'Installing Firebase Tools...'
                bat 'npm install -g firebase-tools'
            }
        }

        stage('Testing') {
            steps {
                echo 'Deploying to Testing...'
                bat 'firebase deploy --only hosting:testing --token %FIREBASE_TOKEN%'
            }
        }

        stage('Staging') {
            steps {
                echo 'Deploying to Staging...'
                bat 'firebase deploy --only hosting:staging --token %FIREBASE_TOKEN%'
            }
        }

        stage('Production') {
            steps {
                echo 'Deploying to Production...'
                bat 'firebase deploy --only hosting:production --token %FIREBASE_TOKEN%'
            }
        }
    }
    post {
        success {
            echo 'Deployment finished successfully!'
        }
        failure {
            echo 'Deployment failed, check the logs!'
        }
    }
}