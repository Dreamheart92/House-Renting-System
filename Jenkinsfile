pipeline{
    agent any

    stages{
        stage('Install .NET 6.0') {
                    steps {
                        script {
                            sh '''
                                if ! dotnet --list-runtimes | grep -q "Microsoft.NETCore.App 6.0"; then
                                    curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin --channel 6.0
                                    export PATH=$PATH:$HOME/.dotnet
                                fi
                            '''
                        }
                    }
                }

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