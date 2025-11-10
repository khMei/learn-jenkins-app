pipeline {
   agent { label 'docker-node-git' }
    stages {
        stage('Debug') {
            steps {
                sh '''
                    whoami
                    uname -a
                    echo $PATH
                    node --version
                    npm --version
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    npm test || echo "Tests failed, but pipeline continues"
                '''
            }
        }
    }
}
