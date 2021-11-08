pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                git "https://github.com/Anil-appari007/dotnettest.git"
                bat "\"${tool 'msbuild'}\" myWebApp/myWebApp.csproj /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release  /p:DeleteExistingFiles=True /p:publishUrl=E:\\testdotnet"
            }
        }
    }
}
