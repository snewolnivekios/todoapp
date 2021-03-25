pipeline {
  environment {
    registry = "snewolk/todoapp"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
  stages {
    /* Clone occurring via config for Pipeline script from SCM
    stage('Cloning git') {
      steps {
        git 'https://github.com/snewolnivekios/todoapp.git'
      }
    }
    */
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
