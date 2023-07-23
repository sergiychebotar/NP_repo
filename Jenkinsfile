pipeline{
    agent any
    options{
        buildDiscarder(logRotator(numToKeepStr: '5', daysToKeepStr: '5'))
        timestamps()
    }
    environment{
        
        registry = "chebik/np-repo"
        registryCredential = 'dockerhub'        
    }
    
    stages{
       stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
       stage('Deploy Image') {
      steps{
         script {
        //    docker.withRegistry( '', registryCredential ) {
        //    dockerImage.push()
        //  }
          withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerhub_psw', usernameVariable: 'dockerhub_usr')]) {
             dockerImage.push()
          }
        }
      }
    }
}
}