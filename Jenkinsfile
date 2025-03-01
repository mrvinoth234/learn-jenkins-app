pipeline {
    agent any

    stages {
        stage('Build') {
            agent {   
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "With Docker"
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    touch container-yes.txt
                '''
            }
        }
        stage('Test') {
            steps{
                sh 'test -f build/index.html'
            }
        }
    }
}
