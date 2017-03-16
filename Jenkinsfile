
node {
   def mvnHome
   def version
   stage('Preparation') {
      git 'https://github.com/SeshagiriSriram/addressbook.git'
      mvnHome = tool 'LOCAL_MAVEN'
      version = '2.3.5'
    }
   stage('UnitTest') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean test"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean test/)
      }
   }
    stage('Code review') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean pmd:pmd"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
    stage('Test Case Coverage') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean cobertura:cobertura"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   
  
} 
