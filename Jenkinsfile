library(identifier: 'utils@v2.4.5', retriever: modernSCM(
  [$class: 'GitSCMSource',
   remote: 'git@github.com:cloudops/cloudmc-jenkins-shared.git',
   credentialsId: 'gh-jenkins']))

pipeline {
  agent { label 'api-docs' }
  options { disableConcurrentBuilds() }

  environment {
    GIT_URL = 'git@github.com:hypertec-cloud/hci-api-docs.git'
  }

  stages {
    stage('Setup') {
      steps {
        deleteDir()
        git credentialsId: 'gh-jenkins', url: env.GIT_URL, branch: env.BRANCH_NAME
      }
    }

    stage('Deploy github pages') {
      when {
        expression {
          env.BRANCH_NAME == 'hci-dev'
        }
      }
      steps{
        script {
            sh "sudo bundle install"
            withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'gh-jenkins', usernameVariable: 'GIT_AUTHOR_NAME', passwordVariable: 'GIT_PASSWORD']]) {
                sh 'set +x'
                sh 'git config user.name "$GIT_AUTHOR_NAME"'
                sh 'git config user.password "$GIT_PASSWORD"'
                sh 'set -x'
                sh "./deploy.sh"
            }
        }
      }
    }
  }
  post{
    always {
      notifySlack currentBuild.result
    }
  }
}

