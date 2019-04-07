node {
    stage('Checkout') {
      git branch: 'master', url: params.git_repo
    }
    stage('Build Docker Image') {
        sh(script: "docker build -t ${params.acr_loginserver}/${params.web_image_name} .", returnStdout: true)
    }
    stage('Push Docker Image') {
        sh(script: "docker push ${params.acr_loginserver}/${params.web_image_name}", returnStdout: true)
    }
    stage('Deploy to Kubernetes') {
        sh(script: "kubectl set image deployment/hello-world hello-world=${params.acr_loginserver}/${params.web_image_name} --kubeconfig /var/lib/jenkins/config", returnStdout: true)
    }
}
