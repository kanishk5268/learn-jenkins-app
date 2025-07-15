pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
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

        stage('Test'){
            steps {
                sh ''' 
                    echo "This is Test stage"
                    test -e "learn-jenkins-app/build/index.html" && echo "File exists" || echo "File does not exist" 
                '''
            }
        }
    }
}
 