node{
   stage('SCM Checkout'){ 
     git 'https://github.com/naveenswathi/Pipeline.git'
   }
   stage('Compile-Package'){
    def mvnHome = tool name: 'MAVEN_HOME', type: 'maven'
    def mvnCMD = "${mvnHome}/bin/mvn"
    sh "${mvnCMD} clean package"
   }  
   stage('Build Docker image'){
     //def var = tool name: 'Docker', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
      sh 'docker build -t naveenswathi/my-web:2.3.0 .'
   }  
   stage('Push Docker image'){
      withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]){
         sh "docker login -u naveenswathi -p ${dockerHubPwd}"
      }  
      sh 'docker push naveenswathi/my-web:2.3.0'
   }  
   stage('Run Container'){
      sh 'docker run -p 8090:8080 -d --name container2 naveenswathi/my-web:2.3.0'
   }  
}   
