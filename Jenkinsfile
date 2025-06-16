pipeline{
    agent any

    stages{
        stage('MS Restore') {
            steps {
                script {
                    // Restore the .NET project
                    sh 'dotnet restore'
                }
            }
        }

        stage ("Build packages") {
            steps {
                script {
                    // Build the .NET project
                    sh 'dotnet build --configuration Release'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests
                    sh 'dotnet test --configuration Release'
                }
            }
        }
    }
}