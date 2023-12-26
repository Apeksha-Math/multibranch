pipeline {
    agent any

    environment {
        // Define any environment variables you may need
        // For example: GIT_REPO_URL = 'https://github.com/Apeksha-Math/Jenkins.git'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout code from Git
                    git branch: 'main', url: 'https://github.com/Apeksha-Math/Jenkins_multibranch.git'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Your build commands go here
                    // For example: sh 'mvn clean install'
                    echo 'Building...'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Your test commands go here
                    // For example: sh 'mvn test'
                    echo 'Testing...'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Check if the branch is a tag
                    if (env.BRANCH_NAME.startsWith('refs/tags/staging')) {
                        // Your staging deployment logic goes here
                        echo 'Deploying to staging...'
                    } else if (env.BRANCH_NAME.startsWith('refs/tags/production')) {
                        // Your production deployment logic goes here
                        echo 'Deploying to production...'
                    } else {
                        // Handle other branches or scenarios
                        echo 'Not deploying. Branch does not match staging or production.'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment succeeded!'
        }
        failure {
            echo 'Build or deployment failed!'
        }
    }
}
