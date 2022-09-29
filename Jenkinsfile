node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github3', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email sopheapphon2001@gmail.com"
                        sh "git config user.name PhonSopheap"
                        sh "cat flask-deployment.yaml"
                        sh "sed -i 's+poretrithynea/miniproject.*+poretrithynea/miniproject:${DOCKERTAG}+g' flask-deployment.yaml"
                        sh "cat flask-deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/configuration.git HEAD:main"
      }
    }
  }
}
}
