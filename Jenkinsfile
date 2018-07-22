node('master') 
{
    stage('ContinuousDownload') 
    {
       git 'https://github.com/naveev/maven-1.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
         sh 'scp /var/lib/jenkins/workspace/tom/webapp/target/webapp.war ubuntu@172.31.28.172:/var/lib/tomcat7/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/TestingOnLinux.git'
        sh 'java -jar /var/lib/jenkins/workspace/tom/testing.jar'
    }
    stage('ContinuousDelivery')
    {
       input message: 'Requesting for approval from DM', submitter: 'admin'
        sh 'scp /var/lib/jenkins/tom/webapp/target/webapp.war ubuntu@172.31.4.140:/var/lib/tomcat7/webapps/prodenv.war'
    }
    
    
    
    
    
    
    
}   
    
    
    
    
