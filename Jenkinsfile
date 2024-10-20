pipeline {
    agent any // Define the agent to be Ubuntu-based

    environment {
        CHROMEWEBDRIVER = "/usr/bin/google-chrome" // Set the environment variable for Chrome WebDriver
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the source code from the repository
                checkout scm
            }
        }
        stage('Install Chrome') {
            steps {
                // Install Google Chrome
                bat '''
                sudo apt-get update
                sudo apt-get install -y google-chrome-stable
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                // Restore dependencies for the solution
                bat 'dotnet restore SeleniumBasicExercise.sln'
            }
        }

        stage('Build Solution') {
            steps {
                // Build the solution without restoring dependencies
                bat 'dotnet build SeleniumBasicExercise.sln --no-restore'
            }
        }

        stage('Run TestProject1 Tests') {
            steps {
                // Run the tests in TestProject1
                bat '''
                echo "Running TestProject1 tests"
                dotnet test TestProject1/TestProject1.csproj --verbosity normal
                '''
            }
        }

        stage('Run TestProject2 Tests') {
            steps {
                // Run the tests in TestProject2
                bat '''
                echo "Running TestProject2 tests"
                dotnet test TestProject2/TestProject2.csproj --verbosity normal
                '''
            }
        }

        stage('Run TestProject3 Tests') {
            steps {
                // Run the tests in TestProject3
                bat '''
                echo "Running TestProject3 tests"
                dotnet test TestProject3/TestProject3.csproj --verbosity normal
                '''
            }
        }
    }
}

