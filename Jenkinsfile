pipeline {
    agent any
    triggers {
        githubPush()
    }
    environment {
        API_TOKEN = credentials('my-api-token')
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
                    echo "Token is: $API_TOKEN"
                    curl -H "Authorization: Bearer $API_TOKEN" https://httpbin.org/get || true
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
