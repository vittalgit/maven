node('selenium')
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/vittalgit/maven.git'
    }
    stage('ContinuousBuild') 
    {
         sh label: '', script: '/home/selenium/tools/hudson.tasks.Maven_MavenInstallation/Maven/bin/mvn package'
    }
    //stage('ContinuousDeployment')
    //{
      //  sh label: '', script: 'scp /home/selenium/workspace/test-v/webapp/target/webapp.war /var/lib/tomcat8/webapps/testenv.war'
    //}
    stage('ContinuousTesting')
    {
        git 'https://github.com/vittalgit/maven.git'
        sh label: '', script: 'java -jar /home/selenium/workspace/test-v/testing.jar'
    }
     stage('ContinuousDelivery')
    {
        input message: 'Waiting for Approval from the DM', submitter: 'Vittal'
        sh label: '', script: 'scp /home/selenium/workspace/test-v/webapp/target/webapp.war /var/lib/tomcat8/webapps/prodenv.war'
    }
    
    
}

