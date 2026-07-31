pipeline
{
    agent any
    stages
    {
        stage('conDownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('conBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('conDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline2/webapp/target/webapp.war ubuntu@172.31.20.1:/var/lib/tomcat10/webapps/testapp.war'
            }
        }
        stage('conTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('conDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline2/webapp/target/webapp.war ubuntu@172.31.17.13:/var/lib/tomcat10/webapps/prodapp.war'
            }
        }
    }
}
