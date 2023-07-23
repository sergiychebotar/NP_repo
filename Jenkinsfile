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
       stage('Deploy Image') {
      steps{
         script {
            withCredentials([usernamePassword(credentialsId: 'DOCKERHUB', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
            //docker.withRegistry( '', 'dockerhub' ) {
            def customImage = docker.build("chebik/np-repo:${env.BUILD_ID}")
            /* Push the container to the custom Registry */
            customImage.push()
            //dockerImage.push()
          }
        }
      }
    }
}
}