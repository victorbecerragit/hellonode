# Updated Jenkinsfile to use kaniko as build/push using pod as agent on jenkins.

Pre-requisites: 
- Kubernetes cluster (kind)
- Setup "kubernetes" plug-ing and cloud node on jenkins.
- Secret dockerregistry token to push image.
  
Guides: 
Jenkins , using pod as agent:
https://gist.github.com/darinpope/67c297b3ccc04c17991b22e1422df45a

Jenkins, using kaniko to build images:
https://gist.github.com/darinpope/f4e52152ce9106610e51fe53ccabe512

# Hello Node
This is a very basic Hello World application written with Node.

It includes a `Dockerfile` for building a Docker image with the application, and a `Jenkinsfile` that defines a build pipeline for it.

https://www.releaseworksacademy.com
