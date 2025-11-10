pipeline {
    agent { label 'docker' }

       stages {
        stage('Debug Host') {
          steps {
               sh'''
                  whoami
                 uname -a
                echo $PATH
                which node
                '''
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
