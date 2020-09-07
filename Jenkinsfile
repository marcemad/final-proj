pipeline {
    agent { docker { image 'python:3.5.1' } }
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
