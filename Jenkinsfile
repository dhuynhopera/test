pipeline {
  agent any
  environment {
    CI_SERVER = 'yes'
    CI_COMMIT_HASH = '${GIT_COMMIT}'
  }
  stages {
    stage('Build & Test') {
      steps {
        script {
          awsCodeBuild(
            projectName: 'poco',
            credentialsType: 'jenkins',
            credentialsId: 'aws-codebuild',
            region: 'use-east-2',
            sourceControlType: 'project',
            sourceVersion: env.BRANCH_NAME,
            buildSpecFile: 'ci/buildspec.build.yml'
          )
        }
      }
    }
  }
}
