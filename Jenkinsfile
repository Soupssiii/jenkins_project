pipeline {
    agent any
    environment { VIRTUAL_ENV = 'venv' }

    stages {
        stage('Setup') {
            steps {
                script {
                    // Create virtual environment
                    bat "\"C:\\Users\\Cirin\\AppData\\Local\\Programs\\Python\\Python312\\python.exe\" -m venv ${VIRTUAL_ENV}"
                    
                    // Upgrade pip safely
                    bat "call ${VIRTUAL_ENV}\\Scripts\\activate && ${VIRTUAL_ENV}\\Scripts\\python.exe -m pip install --upgrade pip"
                    
                    // Install dependencies
                    bat "call ${VIRTUAL_ENV}\\Scripts\\activate && pip install -r requirements.txt"
                }
            }
        }

        stage('Lint') {
            steps {
                bat "call ${VIRTUAL_ENV}\\Scripts\\activate && flake8 app.py"
            }
        }

        stage('Test') {
            steps {
                bat "call ${VIRTUAL_ENV}\\Scripts\\activate && pytest"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
