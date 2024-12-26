pipeline {
    agent {
        any {
            image 'mcr.microsoft.com/dotnet/sdk:9.0'
            args '-u root:root'
        }
    }

    stages {
        stage('Clean workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Restore packages') {
            steps {
                script {
                    if (isUnix()) {
                        sh "dotnet restore ${workspace}/automated-pipeline/projects.sln"
                    } else {
                        bat "dotnet restore ${workspace}\\automated-pipeline\\projects.sln"
                    }
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh "dotnet build ${workspace}/automated-pipeline/projects.sln --configuration Release"
                    } else {
                        bat "dotnet build ${workspace}\\automated-pipeline\\projects.sln --configuration Release"
                    }
                }
            }
        }
        stage('Publish') {
            steps {
                script {
                    if (isUnix()) {
                        sh "dotnet publish ${workspace}/automated-pipeline/projects.sln --configuration Release"
                    } else {
                        bat "dotnet publish ${workspace}\\automated-pipeline\\projects.sln --configuration Release"
                    }
                }
            }
        }
    }
}