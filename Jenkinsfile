pipeline {
    agent {
        label 'dotnet8-agent'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/RohitSingh10000/EmployeeApi.git'
            }
        }

        stage('Restore') {
            steps {
                sh 'dotnet restore EmployeeApi.csproj'
                sh 'dotnet restore EmployeeApi.Tests/EmployeeApi.Tests.csproj'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build EmployeeApi.csproj --configuration Release --no-restore'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test EmployeeApi.Tests/EmployeeApi.Tests.csproj --configuration Release --no-restore'
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline SUCCESS: Build and tests passed!'
        }

        failure {
            echo 'CI Pipeline FAILED: Check the stage logs for errors.'
        }

        always {
            echo 'CI Pipeline execution completed.'
        }
    }
}