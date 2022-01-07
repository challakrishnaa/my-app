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
           sh "${mvnCMD} clean install package"
        }
     }
     stage('deploy into container'){
        steps{
          sshagent(['tomcatdevT']) {
    sh 'scp -o StrictHostKeyChecking=no /home/ec2-user/jenkins/workspace/MULTIJOB_dev/target/myweb-1.0.war 
         }
     }
  
     }
  
  }
}
