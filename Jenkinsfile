pipeline {
	agent any
	environment {
		CI_SERVER = 'yes'
		CI_COMMIT_HASH = '${GIT_COMMIT}'
	}
	stages {
		stage('Build & Test') {
			script { build() }
		}
	}
}

def build() {
	awsCodeBuild(
		projectName: 'poco',
		credentialsType: 'Jenkins',
		credentialsId: 'aws-codebuild',
		region: 'use-east-2',
		sourceControlType: 'project',
		sourceVersion: env.BRANCH_NAME,
		buildSpecFile: 'ci/buildspec.build.yml'
	)
}
