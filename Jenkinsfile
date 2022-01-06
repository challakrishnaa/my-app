pipeline{
   agent{label 'QA-Slave'}
   environment{
   def mvnHOME=tool name: 'maven-3.8', type: 'maven'
      def mvnCMD="${mvnHOME}/bin/mvn"
   }
  stages{
    stage('ECKOUTCODsE'){
      steps{
      git 'https://github.com/challakrishnaa/my-app.git'
      }
    }
     stage('buildcode'){
        steps{
           sh "${mvnCMD} clean package"
        }
     }
     stage('deploy into container'){
        steps{
          sshagent(['Tomcat9-cred']) {
          sh 'scp ssh -o StrictHostKeyChecking=no /workspace/MULTIJOB_master/target/myweb-1.0.war ec2-user@54.242.24.54:/opt/tomcat9/webapps'
        }
     }
  
     }
  
  }
}
