pipeline{
   agent{label 'devslave'}
   environment{
   def mvnHOME=tool name: 'maven-3.8', type: 'maven'
      def mvnCMD="${mvnHOME}/bin/mvn"
   }
  stages{
    stage('ECKOUTCODsE'){
      steps{
      git 'git branch: 'dev', url: 'https://github.com/challakrishnaa/my-app.git''
      }
    }
     stage('buildcode'){
        steps{
           sh "${mvnCMD} clean install package"
        }
     }
     stage('deploy into container'){
        steps{
          sshagent(['Tomcat9-cred']) {
          sh 'scp -o StrictHostKeyChecking=no /home/ec2-user/jenkins/workspace/MULTIJOB_master/target/myweb-1.0.war ec2-user@54.242.24.54:/opt/tomcat9/webapps'
        }
     }
  
     }
  
  }
}
