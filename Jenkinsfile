pipeline {
    agent any
    environment { VIRTUAL_ENV = 'venv' }

    stages {
        stage('Setup') {
            steps {
                script {
                    // Step 1: Create a virtual environment using full Python path
                    bat "\"C:\\Users\\Cirin\\AppData\\Local\\Programs\\Python\\Python312\\python.exe\" -m venv ${VIRTUAL_ENV}"
                    
                    // Step 2: Activate venv and install dependencies
                    bat "call ${VIRTUAL_ENV}\\Scripts\\activate && pip install --upgrade pip && pip install -r requirements.txt"
                }
            }
        }

        stage('Lint') {
            steps {
                // Activate venv and run flake8
                bat "call ${VIRTUAL_ENV}\\Scripts\\activate && flake8 app.py"
            }
        }

        stage('Test') {
            steps {
                // Activate venv and run pytest
                bat "call ${VIRTUAL_ENV}\\Scripts\\activate && pytest"
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying application..."
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
