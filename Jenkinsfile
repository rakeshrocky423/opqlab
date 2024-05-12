pipeline {
    agent any
    tools {
  pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    
    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/rakeshrocky423/shopping-cart.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image'){
            steps {
                sh 'docker build -t rocky07/my-app:2.0.0 .'
            }
            
        }
        stage('Push Docker Image'){
            steps{
               withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
                  sh "docker login -u rocky751 -p ${dockerHubPwd}"
               }
            sh 'docker push rocky751/my-app:2.0.0'
            }
           
        }
        stage('Deploy'){
            steps {
                sh 'docker run -p 8080:8080 -d --name my-app rocky07/my-app:2.0.0'
            }
            
        }
   }
   
}   
