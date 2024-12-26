def workspace = env.WORKSPACE

pipeline {
    agent any

    stages {
        stage('Clean workspace') {
      steps {
        cleanWs()
      }
        }
        stage('Restore packages') {
      steps {
        bat "dotnet restore ${workspace}\\automated-pipeline\\projects.sln"
      }
        }
        stage('Build') {
      steps {
        bat "dotnet build ${workspace}\\automated-pipeline\\projects.sln --configuration Release"
      }
        }
    }
}
