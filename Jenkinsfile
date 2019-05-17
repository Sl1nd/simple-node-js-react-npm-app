pipeline {
    agent any
    environment {
        CI = 'true'
        GH_TOKEN = credentials('github-token')
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install -g npx'
                sh 'npm install'
                sh 'git --version'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh 'npx semantic-release'
            }
        }
    }
}
