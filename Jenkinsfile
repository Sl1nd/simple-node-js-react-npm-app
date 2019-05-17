pipeline {
    agent any
    environment {
        CI = 'true'
        GH_TOKEN = credentials('github-token')
        NODEJS_HOME = "${tool NodeJS8}"
        PATH="${env.NODEJS_HOME}:${env.PATH}"
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo $PATH'
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
