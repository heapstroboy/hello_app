pipeline {
    environment {
        registry = "docker_hub_heapstroboy/hello-service"
        registryCredential = 'dockerhub'
  }
  agent any
  stages {
    stage('Build') {
       steps {
           sh 'mvn clean install'
       }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
        script{
          docker.push registry
        }
      }
    }
  }
}