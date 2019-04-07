node {
    stage('Checkout') {
      git branch: 'master', url: params.git_repo
    }
    stage('Build Docker Image') {
        sh(script: "docker build .", returnStdout: true)
    }
    stage('deploy') {
        azureWebAppPublish azureCredentialsId: params.azure_cred_id,
            resourceGroup: params.res_group, appName: params.helloworldwebapp, sourceDirectory: "bin/Release/netcoreapp2.2/publish/"
    }
}
