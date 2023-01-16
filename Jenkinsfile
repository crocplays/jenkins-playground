#!groovy
pipeline{
    agent none
    stages{
        stage('Docker Build') {
            agent any
            steps{
                sh 'docker build -t chenadi/jenkins-playground:latest .'
            }
        }
        stage('Docker push'){
            agent any 
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh 'docker push chenadi/jenkins-playground:latest'
                }
            }
        }
    }
}