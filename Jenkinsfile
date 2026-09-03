pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t jenkins-ci-project .'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests inside Docker...'
                sh 'docker run --rm jenkins-ci-project'
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'CI Pipeline failed!'
        }
    }
}
