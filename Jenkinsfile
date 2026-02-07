pipeline {
    agent any

    stages {

        stage ('Checkout') {
            steps {
                checkout scm
            }
        }

        stage ('Install Dependencies') {
            steps {
                bat 'uv sync'
                bat 'uv pip install -r requirements.txt'
                bat 'uv pip install pyinstaller'
            }
        }

        stage ('Build exe') {
            steps {
                bat 'pyinstaller --onefile password_gen.py'
            }
        }

        stage ('Archive Installation') {
            steps {
                archiveArtifacts artifacts: 'dist/*.exe'
            }
        }
    }
}