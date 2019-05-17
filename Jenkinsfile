pipeline {
    agent any
    tools {nodejs "NodeJS8"}
    environment {
        GH_TOKEN = credentials('github-token')
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo $GH_TOKEN'
                sh 'echo $GITHUB_URL'
                sh 'npm --version'
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
