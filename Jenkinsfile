pipeline {
    environment {
        registry = "docker_hub_heapstroboy/hello-service"
        registryCredential = 'dockerhub'
  }
  agent any
  stages {
    stage('Cloning Git') {
       steps {
         git 'https://github.com/heapstroboy/hello_app.git'
          }
    stage('Build') {
       steps {
           sh 'mvn clean install'
       }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}