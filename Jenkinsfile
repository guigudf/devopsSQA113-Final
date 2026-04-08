pipeline {
    agent any
    environment {
        FIREBASE_TOKEN = credentials('firebase-token') 
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install -g firebase-tools'
            }
        }
        stage('Testing') {
            steps {
                sh 'echo "Running tests..."'
            }
        }
        stage('Staging') {
            steps {
                sh 'firebase deploy --only hosting:staging --token $FIREBASE_TOKEN'
            }
        }
        stage('Production') {
            steps {
                sh 'firebase deploy --only hosting:production --token $FIREBASE_TOKEN'
            }
        }
    }
}