pipeline {
    agent { docker { image 'node:22.11.0-alpine3.20' } }
    stages {
        stage('build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('test') {
            steps {
                sh 'apt-get update'
                sh 'wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb'
                sh 'apt install -y ./google-chrome*.deb'
                sh 'export CHROME_BIN=/usr/bin/google-chrome'
                sh 'npm install -g @angular/cli@^17.3.8'
                sh 'npm install'
                sh 'npm run test:ci'
            }
        }
    }
}
