pipeline {
    agent { label 'docker' }

       stages {
        stage('Debug Host') {
          steps {
        bat 'whoami'
        bat 'uname -a'
        bat 'echo $PATH'
        bat 'which node'
             }
          }

        stage('Build') {
            steps {
                bat '''
                   apk add --no-cache git openssh ca-certificates
                   update-ca-certificates
                   node --version
                   npm --version
                   npm ci
                   npm run build
                   ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'test stage'
            }
        }
    }
}
