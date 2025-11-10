pipeline {
    agent {
        node { label 'Built-In Node' } // Or whatever your Linux node label is
    }
       stages {
        stage('Debug Host') {
          steps {
              docker.image('node:18-alpine').inside {
               sh'''
                  whoami
                 uname -a
                echo $PATH
                which node
                '''
             }
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
               sh 'npm test || echo "Tests failed, but pipeline continues"'
            }
        }
    }
}
