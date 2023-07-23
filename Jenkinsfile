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
            docker.withRegistry( 'https://registry-1.docker.io/v2/', 'dockerhub' ) {
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