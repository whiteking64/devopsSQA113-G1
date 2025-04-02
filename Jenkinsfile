pipeline {
    agent {
        docker {
            image 'node:20.9.0-alpine3.18'
        }
    }
    environment {
        FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }
    stages {
        stage('Building') {
            steps {
                sh 'npm install -g firebase-tools'
            }
        } 
 
        stage('Testing') {
            steps {
                sh 'firebase deploy -P devops-sqa113-testing --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }
 
        stage('Staging') {
            steps {
                sh 'firebase deploy -P devops-sqa113-staging --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }
 
        stage('Production') {
            steps {
                sh 'firebase deploy -P devops-sqa113-production --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }
    }
}
