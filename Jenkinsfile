pipeline {
    agent any

    environment {
        // ✅ Your actual python path
        PYTHON = 'C:\\Users\\User\\AppData\\Local\\Programs\\Python\\Python313\\python.exe'
    }

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
                bat "\"%PYTHON%\" -m pip install --upgrade pip"
                bat "\"%PYTHON%\" -m pip install -r requirements.txt"
            }
        }

        stage('Run Tests') {
            steps {
                echo "Running pytest..."
                bat "\"%PYTHON%\" -m pytest -v"
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
