pipeline{
  agent any
  stages{
    stage("Git Checkout"){
      steps{
            git url: 'https://github.com/aditya-malviya/myweb.git'
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
          sshagent(['18.205.115.52']) {
          sh """
          scp -o StrictHostKeyChecking=no target/mcs.war  
          admin@18.205.115.52:/opt/tomcat/webapps/
          ssh admin@18.205.115.52 /opt/tomcat/bin/shutdown.sh
          ssh admin@18.205.115.52 /opt/tomcat/bin/startup.sh
           """
            }
          }
        }
  }
}
