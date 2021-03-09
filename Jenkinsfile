pipeline {
  agent any
    
  tools {nodejs "node"}
    
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
        def customImage = docker.build("smaple-node:${env.BUILD_ID}")

      }
    }

  }
}