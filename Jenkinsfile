node{
   stage('SCM Checkout'){
     git 'https://github.com/deepthinbr01/samplemav.git'
   }
    stage('MVN package'){
     sh 'mvn package'
}

   stage('Build Docker Image'){
     sh 'mvn package'
}
  stage('Build Docker Imager'){
   sh 'docker build -t deepthinbr01/my-app:0.0.1 .'
 }

  stage(' push Docker image'){
   withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
    sh "docker login -u deepthinbr01 -p ${dockerHubPwd}"
     }
      sh 'docker push deepthinbr01/my-app:0.0.1'

}
 



}
