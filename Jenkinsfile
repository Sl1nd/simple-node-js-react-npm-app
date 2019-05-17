pipeline {
    agent any
    environment {
        CI = 'true'
        GH_TOKEN = credentials('github-token')
        env.NODEJS_HOME = tool "NodeJS8"
        env.PATH="${env.NODEJS_HOME}/bin:${env.PATH}"
        sh 'npm --version'
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
