pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build Solution') {
            steps {
                bat 'dotnet build  --no-restore'
            }
        }

        stage('Run Ui tests') {
            steps {
                bat 'dotnet test'
            }
        }
    }
}
