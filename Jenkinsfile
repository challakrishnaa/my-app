pipeline{
   agent{label 'uatslave'}
   environment{
   def mvnHOME=tool name: 'maven-3.8', type: 'maven'
      def mvnCMD="${mvnHOME}/bin/mvn"
   }
  stages{
    stage('ECKOUTCODsE'){
      steps{
      git branch: 'uat', url: 'https://github.com/challakrishnaa/my-app.git'
      }
    }
     stage('buildcode'){
        steps{
           sh "${mvnCMD} clean install package"
        }
     }
     stage('deploy into container'){
        steps{
          sshagent(['uatslave']) {
          sh 'scp -o StrictHostKeyChecking=no ./*.war ec2-user@54.166.93.221:/opt/tomcat8/webapps'
        }
     }
  
     }
  
  }
}
