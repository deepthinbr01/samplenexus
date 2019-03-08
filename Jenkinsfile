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
      stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 8080:8080 -d --name my-app deepthinbr01/my-app:2.0.0'
     sshagent(credentials: ['dev-server'], ignoreMissing: true) {
  
        sh "ssh -o StrictHostKeyChecking=no deepthimurali01@10.142.0.18 ${dockerRun}"
     }


}
