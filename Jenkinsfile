pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                git "https://github.com/Anil-appari007/dotnettest.git"
            }
        }
        stage('Code Quality Check via SonarQube'){
            environment {
                scannerHome = tool 'sonarqube-on-vm'
            }
            steps{
                
                bat "   ${scannerHome}\\bin\\sonar-scanner \
                          -Dsonar.projectKey=Dotnet-test \
                          -Dsonar.sources=. \
                          -Dsonar.css.node=. \
                          -Dsonar.host.url=http://localhost:9000 \
                          -Dsonar.login=f899418a1acffeaf6ff566165f7ad9a90b71e26b"
            }
        }
        stage("Build With MSBUILD"){
            steps{
                bat "\"${tool 'msbuild'}\" myWebApp/myWebApp.csproj /p:DeployOnBuild=true /p:DeployDefaultTarget=WebPublish /p:WebPublishMethod=FileSystem /p:SkipInvalidConfigurations=true /t:build /p:Configuration=Release  /p:DeleteExistingFiles=True /p:publishUrl=E:\\testdotnet"
            }
        }
    }
}
