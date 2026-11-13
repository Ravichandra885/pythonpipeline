
pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compilation') {
            steps {
                bat '"C:\\Users\\dell\\AppData\\Local\\Programs\\Python\\Python310\\python.exe" -m py_compile app.py test_app.py'
            }
        }

        stage('Testing') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Execution') {
            steps {
                bat '"C:\\Users\\dell\\AppData\\Local\\Programs\\Python\\Python310\\python.exe" app.py'
            }
        }

        stage('Packaging') {
            steps {
                bat 'if not exist dist mkdir dist'
                bat 'powershell -Command "Compress-Archive -Path app.py -DestinationPath dist\\python-app.zip -Force"'
                archiveArtifacts artifacts: 'dist/*.zip'
            }
        }
    }
}
