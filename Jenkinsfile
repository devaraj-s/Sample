#!/usr/bin/groovy

podTemplate(yaml: """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: docker
    image: docker:1.11
    command: ['cat']
    tty: true
    volumeMounts:
    - name: dockersock
      mountPath: /var/run/docker.sock
  volumes:
  - name: dockersock
    hostPath:
      path: /var/run/docker.sock
"""
  ) {
  def image = "devarajsuk/express-node"
  node(POD_LABEL) {
    stage('Build Docker image') {
      checkout scm
      container('docker') {
        sh "docker build -t ${image} ."
      }
    }
  }
}