node{
   stage('SCM Checkout'){ 
     git 'https://github.com/naveenswathi/Pipeline.git'
   }
   stage('Compile-Package'){
    def mvnHome = tool name: 'MAVEN_HOME', type: 'maven'
    sh "${mvnHome}/bin/mvn package"
   }  
}   
