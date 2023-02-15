pipeline {
 agent any
  options {
        timeout(time: 20, unit: 'MINUTES')
        timestamps()
    }
  
  stages {
   
    stage ('build image') {
      steps {
        sh "docker build -t apache:${BUILD_NUMBER} ."
        sh "docker inspect apache:${BUILD_NUMBER}"
      }
    }
    stage('build container') {
      steps {
        sh "docker run -d -p 8081:8080 --name webserver apache:${BUILD_NUMBER}"
        sh "docker ps -a"
       sh"docker images"
       sh "docker logs webserver"
      }
    }
  }
}
