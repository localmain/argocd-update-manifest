node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GITHUB') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    //withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')]) {
   
                    withCredentials([usernamePassword(credentialsId: 'localmain-github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email abhijeetmohanty798@gmail.com"
                        sh "git config user.name localmain"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+34.228.37.180:9090/argocd-dev/localmain.*+34.228.37.180:9090/argocd-dev/localmain deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update manifest "
                        sh "git push --force https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/argocd-update-manifest.git HEAD:main"
                        
                        
      }
    }
  }
}
}
