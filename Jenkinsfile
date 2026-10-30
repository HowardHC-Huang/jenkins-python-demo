pipeline {

    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Environment Check') {
            steps {
                echo 'Checking Windows environment...'

                bat 'whoami'
                bat 'where git'
                bat 'where python'
                bat 'python --version'
            }
        }

        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
        
                checkout scm
        
                bat 'dir'
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Python files...'

                bat 'python -m py_compile app.py test_app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Python unit tests...'

                bat 'python -m unittest discover -v'
            }
        }

    }

    post {
        success {
            echo 'PIPELINE SUCCESS!'
        }

        failure {
            echo 'PIPELINE FAILURE!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}