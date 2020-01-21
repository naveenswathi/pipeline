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
      def var = tool name: 'Docker', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
      sh 'docker build -t naveenswathi/pipeline:2.2.0 .'
   }  
   stage('Push Docker image'){
      withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]){
         sh "docker login -u naveenswathi -p ${dockerHubPwd}"
      }  
      def var = tool name: 'Docker', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
      sh 'dokcer push naveenswathi/pipeline:2.2.0'
   }  
}   
