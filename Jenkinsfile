pipeline{
  agent any
  stages {
    stage ('Docker Build'){
      steps {
        script {
          dockerapp = docker.build("micheldonencio/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
        }
      }
    }  
    stage ('Docker Push'){
      steps {
         script {
           docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
           dockerapp.push('latest')
           dockerapp.push("${env.BUILD_ID}")
         }
      }
    }
  }	
}
