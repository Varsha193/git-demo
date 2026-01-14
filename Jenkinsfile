pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Pulling code from GitHub..."
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing Python requirements..."
                bat 'python -m pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo "Running pytest..."
                bat 'pytest -v'
            }
        }
    }

    post {
        success {
            echo "✅ Build + Tests Passed"
        }
        failure {
            echo "❌ Build Failed. Check logs."
        }
    }
}
