node
{
     def mavenHome = tool name: "maven-3.8.1"

     stage ('checkout')
     {
        git branch: 'development',
        credentialsId: '298480c4-0c1f-48b2-99c3-e08b361b7188',
        url: 'https://github.com/naeem4github/origin.git'
     }
     
     stage('Build')
     {
         sh "${mavenHome}/bin/mvn clean package"
     }
     
/*
     stage('ExecuteSonarQubeReport')
     {
         sh "${mavenHome}/bin/mvn clean sonar:sonar"
     }
     
     stage('UploadArtificatsintoNexus')
     {
         sh "${mavenHome}/bin/mvn deploy"
     }
     
*/
     stage('DeployAppIntoTomcatServer')
     {
      sshagent(['2de836d7-742d-4f93-b9d6-43c967d1d113']) {
      sh "scp -o  StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.17.180.47:/opt/apache-tomcat-9.0.46/webapps/"
      }
     }
}
