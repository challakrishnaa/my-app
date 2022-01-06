pipeline{
   agent{label 'QA-Slave'}
   envirnonment{
   def mvnHOME=tool name: 'maven-3.8', type: 'maven'
      def mvnCMD="${mvnHOME}/bin/mvn"
   }
  stages{
    stage('ECKOUTCODE'){
      steps{
      git 'https://github.com/challakrishnaa/my-app.git'
      }
    }
     stage('buildcode'){
        steps{
        sh 'mvn clean package' 
        }
     }
  
  
  }
}
