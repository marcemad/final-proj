pipeline {
    agent any
    stages {
	stage('Lint Dockerfile') {
	    steps {
                sh 'hadolint Dockerfile'
            }
        }
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
