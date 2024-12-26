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
        script {
          if (isUnix()) {
            sh "dotnetRestore  ${workspace}/automated-pipeline/projects.sln"
                    } else {
            bat "dotnetRestore  ${workspace}\\automated-pipeline\\projects.sln"
          }
        }
      }
        }
        stage('Build') {
      steps {
        script {
          if (isUnix()) {
            sh "dotnetBuild  ${workspace}/automated-pipeline/projects.sln --configuration Release"
                    } else {
            bat "dotnetBuild  ${workspace}\\automated-pipeline\\projects.sln --configuration Release"
          }
        }
      }
        }
    }
}
