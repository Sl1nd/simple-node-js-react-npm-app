pipeline {
    agent any
    tools {nodejs "NodeJS8"}
    environment {
        CI = 'true'
        GH_TOKEN = credentials('github-token')
        GH_URL = 'https://github.com/Sl1nd/simple-node-js-react-npm-app'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo $GH_TOKEN'
                sh 'echo $GH_URL'
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
