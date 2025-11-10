pipeline {
    agent {
        docker {
            image 'node:18-alpine'
            reuseNode true
        }
    }

       stages {
        stage('Debug Host') {
          steps {
        sh 'whoami'
        sh 'uname -a'
        sh 'echo $PATH'
        sh 'which node'
             }
          }

        stage('Build') {
            steps {
                sh '''
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
