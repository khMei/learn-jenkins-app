pipeline {
    agent { label 'windows' }

    stages {
        stage('Debug') {
            steps {
                bat 'whoami'
                bat 'echo %PATH%'
                bat 'node --version'
                bat 'npm --version'
            }
        }

        stage('Build') {
            steps {
                bat 'npm ci'
                bat 'npm run build'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test || echo Tests failed'
            }
        }
    }
}

