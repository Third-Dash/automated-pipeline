stages {
        stage ('Clean workspace') {
            steps {
              cleanWs()
            }
        }
  // stage ('Git Checkout') {
  //   steps {
  //       git branch: 'master', credentialsId: '', url: '<url to your GitHub repository'
  //     }
  //   }
        stage('Restore packages') {
            steps {
              bat "dotnet restore ${workspace}\\automated-pipeline\\projects.sln"
            }
  }
        stage('Clean') {
          steps {
            bat "msbuild.exe ${workspace}\\automated-pipeline\\projects.sln" /nologo /nr:false /p:platform=\"x64\" /p:configuration=\"release\" /t:clean"
          }
        }
 // stage('Increase version') {
 //     steps {
 //         echo "${env.BUILD_NUMBER}"
 //         powershell '''
 //            $xmlFileName = "<path-to-solution>\\<package-project-name>\\Package.appxmanifest"
 //            [xml]$xmlDoc = Get-Content $xmlFileName
 //            $version = $xmlDoc.Package.Identity.Version
 //            $trimmedVersion = $version -replace '.[0-9]+$', '.'
 //            $xmlDoc.Package.Identity.Version = $trimmedVersion + ${env:BUILD_NUMBER}
 //            echo 'New version:' $xmlDoc.Package.Identity.Version
 //            $xmlDoc.Save($xmlFileName)
 //         '''
 //      }
 //  }
          stage('Build') {
          steps {
            bat "msbuild.exe ${workspace}\\automated-pipeline\\projects.sln /nologo /nr:false  /p:platform=\"x64\" /p:configuration=\"release\" /t:clean;restore;rebuild"
          }
          }
}
