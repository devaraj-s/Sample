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
        container('docker') {
          sh """
             docker build -t sample-node:$BUILD_NUMBER .
          """
        }
      }
    }

  }
}