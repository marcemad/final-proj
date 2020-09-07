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
                  sh 'docker build -t capstone-marc .'
              }
         }
         stage('Push Docker Image') {
              steps {
                  withDockerRegistry([url: "", credentialsId: "dockerhub"]) {
                      sh "docker tag capstone-marc marcemad/capstone-marc"
                      sh 'docker push marcemad/capstone-marc'
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
