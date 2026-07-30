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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '0f046bc3-6b40-401e-aafb-e3ac0ce0a4cf', path: '', url: 'http://172.31.20.1:8080')], contextPath: 'mytestapp', war: '**/*.war'
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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '0f046bc3-6b40-401e-aafb-e3ac0ce0a4cf', path: '', url: 'http://172.31.17.13:8080')], contextPath: 'myprodapp', war: '**/*.war'
             }
        }
    }
}
