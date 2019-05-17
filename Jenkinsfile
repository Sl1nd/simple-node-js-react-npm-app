pipeline {
    agent any
    environment {
        CI = 'true'
        GH_TOKEN = credentials('github-token')
        def nodeJSHome = tool 'NodeJS8'
        env.PATH = "${nodeJSHome}/bin:/${env.P<ath}:/tmp/npm-roaming/npm"
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
