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
        sshagent(['ec2-user']) {
       sh 'ssh -o StrictHostKeyChecking=no /target/*.war ec2-user@54.242.24.54:8080:/tomcat9/webapps'
           }
        }
     }
  
  
  }
}
