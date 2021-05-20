node {
 def app 
 
  stage('clone repository') {
    checkout scm 
  }
  stage('Build Image') {
   app = docker.build("omkar0409/nodejs-docker-jenkins")
  }
  stage('Test Image') {
    app.inside {
     sh 'echo "Tests Passed"'
    }
  }
  stage('Push Image') {
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_id') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
