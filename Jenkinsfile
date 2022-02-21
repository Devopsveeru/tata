pipeline{
  agent any
  stages{
    stage("Git Checkout"){
      steps{
            git url: 'https://github.com/Devopsveeru/tata.git'
           }
          }
    stage("Maven Build"){
       steps{
            sh "mvn clean package"
            sh "mv target/*.war target/mcs.war"
             }
            }
        stage("deploy-Apache"){
       steps{
          sshagent(['54.167.135.17']) {
          sh """
          scp -o StrictHostKeyChecking=no target/mcs.war  
          veera@54.167.135.17:/opt/tomcat/webapps/
          ssh veera@54.167.135.17 /opt/tomcat/bin/shutdown.sh
          ssh veera@54.167.135.17 /opt/tomcat/bin/startup.sh
           """
            }
          }
        }
  }
}
