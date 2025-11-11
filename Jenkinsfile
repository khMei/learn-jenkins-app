pipeline {
    agent any
    // {
    // label 'docker' }
    // docker { 
    //     image 'node:18-alpine' 
    //     args '-u root:root' } 
    stages {
        // stage('Debug') {
        //     steps {
        //         sh '''
        //             whoami
        //             uname -a
        //             echo $PATH
        //             node --version
        //             npm --version
        //         '''
        //     }
        // }

        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                // sh '''
                //     npm ci
                //     npm run build
                //     ls -la
                // '''
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
        //     agent {
        //         docker { 
        //             image 'node:18-alpine' 
        //             args '-u root:root' 
        //         }
        //     }
              steps {
        //         sh '''
        //             npm test || echo "Tests failed, but pipeline continues"
        //         '''
                      echo' test stage'
          }
         }
    }
}
