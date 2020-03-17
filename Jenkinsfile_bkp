node{
   stage('SCM Checkout'){
     git 'https://github.com/sudharshanan/hello-world'
   }
   stage('Compile-Package'){
      // Get maven home path
      def MAVEN_HOME =  tool name: 'MAVEN_HOME', type: 'MAVEN_HOME'   
      sh "${MAVEN_HOME}/bin/mvn package"
      //sh "mvn clean package"
   }
   stage('Deploy to Tomcat'){
      
      sshagent(['jenkins_node']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war jenkins@192.68.56.102:/home/jenkins/tomcat/webapps/'
      }
   }
}
