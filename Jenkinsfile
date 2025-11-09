pipeline {
    agent any
    environment { 
        VIRTUAL_ENV = 'venv'
    }

    stages {
        stage('Setup') {
            steps {
                script {
                    // Create venv and install dependencies
                    bat "\"C:\\Users\\Cirin\\AppData\\Local\\Programs\\Python\\Python312\\python.exe\" -m venv ${VIRTUAL_ENV}"
                    bat "call ${VIRTUAL_ENV}\\Scripts\\activate && ${VIRTUAL_ENV}\\Scripts\\python.exe -m pip install --upgrade pip"
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

        stage('Coverage') {
            steps {
                bat "call ${VIRTUAL_ENV}\\Scripts\\activate && coverage run -m pytest && coverage report"
            }
        }

        stage('Security Scan') {
            steps {
                bat "call ${VIRTUAL_ENV}\\Scripts\\activate && bandit -r ."
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
