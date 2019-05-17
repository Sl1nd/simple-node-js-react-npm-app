    node {
        env.CI = 'true'
        env.GH_TOKEN = credentials('github-token')
        env.NODEJS_HOME = tool "NodeJS8"
        // on linux / mac
        env.PATH="${env.NODEJS_HOME}/bin:${env.PATH}"


         stage('Build') {
            sh 'npm --version'

         }

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
