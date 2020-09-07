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
                sh 'hadolint Dockerfile --ignore DL4000'
            }
        }
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
