
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
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      
   }
     stage('Publish') {
     nexusPublisher nexusInstanceId: 'Nexus', nexusRepositoryId: 'release_qa', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'addressbook_main/target/addressbook.war']], mavenCoordinate: [artifactId: 'addressbook_main', groupId: 'com.edurekademo.tutorial', packaging: 'war', version: version]]]
   }
} 
