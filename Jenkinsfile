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
                bat 'firebase deploy --only hosting:testing-site-d76e1 --token %FIREBASE_TOKEN%'
            }
        }
        stage('Staging') {
            steps {
                echo 'Deploying to Staging...'
                bat 'firebase deploy --only hosting:staging-site-f9642 --token %FIREBASE_TOKEN%'
            }
        }
        stage('Production') {
            steps {
                echo 'Deploying to Production...'
                bat 'firebase deploy --only hosting:production-site-dc6c5 --token %FIREBASE_TOKEN%'
            }
        }
    }
}