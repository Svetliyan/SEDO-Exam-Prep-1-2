pipeline {
    agent any
    environment {
        PATH = "/usr/local/share/dotnet:${env.PATH}"
    }

    stages{
        stage("Restore dependencies"){
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                sh 'dotnet restore'
            }
        }
        stage("Build the app"){
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                sh 'dotnet build --no-restore'
            }
        }
        stage("Run the tests"){
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
