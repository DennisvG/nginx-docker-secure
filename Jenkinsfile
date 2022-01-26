@Library(['duo-shared-libraries@master', 'security-libraries']) _

pipeline {
  environment {
    // imageRegisterUrl empty for using default Dockerhub 
    imageRegisterUrl = ''
    imageRegisterCredentials = 'Dockerhub'
    imageName = "dengruns/${BRANCH_NAME}"
    dockerFileName = "Dockerfile.${BRANCH_NAME}"
    imageVersion = '0.1.0'
    dockerImage=''
  }
  
  agent any
  
  stages {
    stage('Build docker image') {
      steps {
        milestone 0
        sh '''echo \'Create docker image\' '''
        script {
            dockerImage = docker.build ("${imageName}:${imageVersion}", "-f ${dockerFileName} .")
        }
      }
    }
    stage('Push docker image') {
      steps {
        milestone 1
        sh '''echo \'Push image to imageRegisterUrl\' '''
        script {
          docker.withRegistry(imageRegisterUrl, imageRegisterCredentials ) {
            // push image with tag ${imageVersion}
            dockerImage.push()
            // push image with tag 'latest'
            dockerImage.push('latest')
          }
        }
      }
    }
  }
  
  post {
    cleanup {
      cleanWs()
      dir("${workspace}@tmp") {
        deleteDir()
      }
    }
  }
}