node('master') 
{
    stage('ContinuousDownload')
    {
       git 'https://github.com/vaishnavi972/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
    sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.27.210:/var/lib/tomcat8/webapps/test.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/vaishnavi972/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
    sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.28.238:/var/lib/tomcat8/webapps/prod.war'
    }
}
