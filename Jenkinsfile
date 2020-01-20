node{
   stage('SCM Checkout'){ 
     git 'https://github.com/naveenswathi/Pipeline.git'
   }
   stage('Compile-Package'){
    def mvnHome = tool name: 'MAVEN_HOME', type: 'maven'
    def mvnCMD = "${mvnHome}/bin/mvn"
    sh "${mvnCMD} clean package"
   }  
}   
