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
   sh 'docker build -t deepthinbr01/myweb:0.0.1 .'
 }
}
