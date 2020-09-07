pipeline {
    agent any
    stages {
        stage('Build') { 
            steps { 
                sh 'ls -a' 
            }
        }

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
