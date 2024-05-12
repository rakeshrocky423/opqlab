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
