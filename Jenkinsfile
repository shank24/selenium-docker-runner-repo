pipeline{
  agent any
    stages {
      stage("Starting Grid") {
        steps{
            sh "docker-compose up -d hub chrome firefox"
        }
      }
      stage("Run Test"){
        steps{
          sh "docker-compose up search-module book-flight-module"
        }
      }
  }
  post{
    always{
        archiveArtifacts artifacts: 'output/**'
        sh "docker-compose down"
    }
  }
}