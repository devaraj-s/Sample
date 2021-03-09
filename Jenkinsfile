pipeline {
  agent any
    
  tools {nodejs "node"}

  environment {
    imagename = "devarajs/samplen-node"
    registryCredential = 'yenigul-dockerhub'
    dockerImage = ''
}
    
  stages {
        
    stage('Git') {
      steps {
        checkout scm
      }
    }
     
    stage('Build') {
    //   steps {
    //     sh 'npm install'
    //   }
    
     steps {
        dockerImage = docker.build imagename
      }
    }

  }
}