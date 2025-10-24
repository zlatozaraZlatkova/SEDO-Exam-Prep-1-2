pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Restore dependencies') {
            when { branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP" }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            when { branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP" }
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        
        stage('Test') {
            when { branch pattern: "(main|develop|feature/.*)", comparator: "REGEXP" }
            steps {
                bat 'dotnet test --no-build --verbosity normal"'
            }
        }
        
    }
}