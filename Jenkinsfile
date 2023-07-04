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
                sh "docker tag mynotesapp:1.0 ${env.dockerHubUser}/mynotesapp:1.0"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/mynotesapp:1.0"
            }   
            }         
        }
        stage("Deploy to dev server"){
            steps{
                sh "docker run -d -p 8000:8000 ${env.dockerHubUser}/mynotesapp:1.0"
            }
        }
    }
}