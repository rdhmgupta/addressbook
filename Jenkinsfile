
node {
   def mvnHome
   def version
   stage('Preparation') {
      git 'https://github.com/SeshagiriSriram/addressbook.git'
      mvnHome = tool 'LOCAL_MAVEN'
      version = '2.3.5'
      
   }
   stage('UnitTest') {
      
         sh "'${mvnHome}/bin/mvn' test"
     
   }
} 
