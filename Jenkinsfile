pipeline {
    agent any
    triggers {
        githubPush()
    }
    environment {
        MY_API_TOKEN_SECRET = credentials('my-api-token')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building the app...'
                sh 'echo build complete'
            }
        }
        stage('Use Credential') {
            steps {
                sh '''
                    echo "Using API token..."
                    echo "Token is: $MY_API_TOKEN_SECRET"
                    curl -H "Authorization: Bearer $MY_API_TOKEN_SECRET" https://httpbin.org/get || true
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'echo all tests passed'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
