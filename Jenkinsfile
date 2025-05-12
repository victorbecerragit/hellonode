
pipeline {
  agent {
    kubernetes {
      yaml """
kind: Pod
spec:
  containers:
  - name: kaniko
    image: gcr.io/kaniko-project/executor:debug
    imagePullPolicy: Always
    command:
    - sleep
    args:
    - 9999999
    volumeMounts:
      - name: jenkins-docker-cfg
        mountPath: /kaniko/.docker
  volumes:
  - name: jenkins-docker-cfg
    projected:
      sources:
      - secret:
          name: docker-credentials
          items:
            - key: .dockerconfigjson
              path: config.json
"""
    }
  }
  stages {
    stage('Clone repository') {
      steps {
        /* Let's make sure we have the repository cloned to our workspace */
        checkout scm
      }  
    }
    
    stage('Build image with Kaniko') {    
      steps {
        /* This builds and push the actual image; synonymous to * docker build and docker push on the command line */
        container(name: 'kaniko', shell: '/busybox/sh') {
          sh '''#!/busybox/sh
            /kaniko/executor --context `pwd` --destination victorbecerra/hello-node:latest
          '''
        }
      }
    }
  }
}

