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

         stage('Build Docker Image') {
              steps {
                  sh 'docker build -t capstoneMarc .'
              }
         }
         stage('Push Docker Image') {
              steps {
                  withDockerRegistry([url: "", credentialsId: "dockerhub"]) {
                      sh "docker tag capstoneMarc marcemad/capstoneMarc"
                      sh 'docker push marcemad/capstoneMarc'
                  }
              }
         }
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
}
