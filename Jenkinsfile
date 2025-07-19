pipeline {
    agent { docker { image 'node:22' } }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayank7924/jenkins-test.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm install vercel'
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([string(credentialsId: 'vercel-token', variable: 'VERCEL_TOKEN')]) {
                    sh 'vercel deploy --prebuilt --token=$VERCEL_TOKEN'
                }
            }
        }
    }
}