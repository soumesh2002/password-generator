pipeline {
    agent any

    stages {

        stage ('Checkout') {
            steps {
                checkout scm
            }
        }

        stage ("Check UV") {
            steps {
                bat 'uv --version'
            }
        }

        stage ('Install Dependencies') {
            steps {
                bat 'uv sync'
            }
        }

        stage ('Build exe') {
            steps {
                bat 'uv run pyinstaller --onefile password_gen.py'
            }
        }

        stage ('Archive Installation') {
            steps {
                archiveArtifacts artifacts: 'dist/*.exe'
            }
        }
    }
}