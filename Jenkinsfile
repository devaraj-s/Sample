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
     
    stage('Initialize'){
        def dockerHome = tool 'docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }

    stage('Build') {
    //   steps {
    //     sh 'npm install'
    //   }
    
     steps {
         script{
            myapp = docker.build("devarajsuk/expresssample:${env.BUILD_ID}")
         }
      }
    }
        stage("Push image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

  }
}