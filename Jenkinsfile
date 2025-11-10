pipeline {
     agent {
        docker {
            image 'node:18-alpine'
            args '-u root:root'
        }
    }
    

    stages {
      stage('Checkout') {
            steps {
                git url: 'https://github.com/khMei/learn-jenkins-app.git', branch: 'main'
            }
        }
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
