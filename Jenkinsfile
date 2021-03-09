#!/usr/bin/groovy

podTemplate(
  label: 'jenkins-pipeline', 
  inheritFrom: 'default',
  containers: [
    containerTemplate(name: 'ng', image: 'alexsuch/angular-cli:1.6.1', command: 'cat', ttyEnabled: true)
  ]
) {
  node ('jenkins-pipeline') {
    stage ('Get Latest') {
      checkout scm
     
      
    }
    stage('Build'){
         script{
                def dockerHome = tool 'docker'
                env.PATH = "${dockerHome}/bin:${env.PATH}"
                def customImage = docker.build("my-image:${env.BUILD_ID}")
                customImage.push()
            }
    }

    // stage ('Build') {
    //   container ('ng') {
    //     sh "npm install"
    //     sh "ng build"
    //   }
    // }
  } // end node
} // end podTemplate