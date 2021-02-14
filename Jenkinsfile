 pipeline{
    agent any
  environment{
   PATH = "/opt/maven/bin:$PATH"
  }
    stages{
        stage('Git-checkout'){
            steps{
                git 'https://github.com/babu-alt/indedx.git'
            }
        }
        stage('Maven Build'){
            agent{label "Node"}
            steps{
                sh "mvn clean package" (if this command not working  then : mvn -f <path of pom.xml file > clean package )
            }
        }
    }
}
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
 pipeline{
    agent any
    
    environment{
       PATH = "/opt/maven/bin:$PATH" 
    }
    stages{
        stage("Git-checkout"){
            steps{
                git 'https://github.com/yankils/hello-world.git' 
            }
        }
        stage("Maven Build"){
            steps{
                sh 'mvn   clean package'
            }
        }
        stage('Deploy to tomcat'){
            steps{
                sshagent(['tomcat-new']) {
                    sh """
                      scp  /var/lib/jenkins/workspace/new_job/webapp/target/webapp.war jenkins@172.31.30.65:/opt/tomcat/webapps
                      ssh jenkins@172.31.30.65  /opt/tomcat/bin/shutdown.sh
                      ssh jenkins@172.31.30.65  /opt/tomcat/bin/startup.sh
                    """
                }
            }
        }
    }
}
