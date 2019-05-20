pipeline {
    agent any
    tools {nodejs "NodeJS8"}
    environment {
        GH_TOKEN = credentials('github-token')
        CI = 'true'
        GIT_BRANCH = 'master'
    }
    stages {
        stage('Build') {
            steps {
                sh 'git branch'
                sh 'echo $BRANCH_NAME'
                sh 'echo $GH_TOKEN'

                sh 'echo $GIT_BRANCH'
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
                sh 'npx semantic-release --debug'
            }
        }
    }
}
