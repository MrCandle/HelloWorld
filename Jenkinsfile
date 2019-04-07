node {
    stage('Checkout') {
      git branch: 'master', url: params.git_repo
    }
    stage('publish') {
        sh(script: "dotnet publish HelloWorld.csproj -c Release ", returnStdout: true)
    }
    stage('deploy') {
        azureWebAppPublish azureCredentialsId: params.azure_cred_id,
            resourceGroup: params.res_group, appName: params.helloworldwebapp, sourceDirectory: "bin/Release/netcoreapp2.2/publish/"
    }
}
