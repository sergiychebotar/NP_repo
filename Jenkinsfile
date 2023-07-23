pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5', daysToKeepStr: '5'))
        timestamps()
    }
    
    stages{
       stage('Building image') {
      steps{
        script {
          dockerImage = docker.build "chebik/np-repo" + ":$BUILD_NUMBER"
        }
      }
    }
  }
}