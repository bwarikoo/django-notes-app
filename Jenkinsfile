pipeline {
    agent any
    stages {
        stage("Code Build"){
            steps{
                sh "docker build . -t mynotesapp:1.0"
            }
        }
        stage("Push Artifacts to DockerHub"){
            steps{
                withCredentials([usernamePassword(credentialsId:"DockerHub",passwordVariable:"DockerHubPass",usernameVariable:"DockerHubUser")]){
                sh "docker tag mynotesapp ${env.dockerHubUser}/mynotesapp:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/mynotesapp:latest"
            }   
            }         
        }
    }
}