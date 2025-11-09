pipeline {
    agent any
    environment { 
        VIRTUAL_ENV = 'venv'
    }

    stages {
        stage('Setup') {
            steps {
                script {
                    if (!fileExists("${env.WORKSPACE}\\${VIRTUAL_ENV}")) {
                        bat "\"C:\\Users\\Cirin\\AppData\\Local\\Programs\\Python\\Python312\\python.exe\" -m venv venv"
                    }
                    bat "call venv\\Scripts\\activate && pip install -r requirements.txt"
                }
            }
        }

        stage('Lint') {
            steps {
                script {
                    bat "call venv\\Scripts\\activate && flake8 app.py"
                }
            }
        }

        
        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying application...'
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
