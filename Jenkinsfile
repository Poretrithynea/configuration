node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github3', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email rotanakkosal03@gmail.com"
                        sh "git config user.name Rotanakkosal"
                        sh "cat deployment.yaml"
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
