pipeline {
    agent any
    stages {
        stage('listing files') { 
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
         stage('Deploying') {
              steps{
                  echo 'Deploying to AWS...'
                  withAWS(credentials: 'aws-static', region: 'us-east-2') {
                      sh "aws eks --region us-east-2 update-kubeconfig --name my-cluster"
                      sh "kubectl config use-context arn:aws:eks:us-east-2:252521120624:cluster/my-cluster"
                      sh "kubectl apply -f deployment.yml"
                      sh "kubectl get nodes"
                      sh "kubectl get deployment"
                      sh "kubectl get pod -o wide"
                      sh "kubectl get service/capstone-marc"
                  }
              }
        }

        stage('any final test') {
            steps {
                sh 'python --version'
            }
        }
    }
}
