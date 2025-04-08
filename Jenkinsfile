pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
               git 'https://github.com/IntelliqDevops/maven.git' 
            }
        }
        stage('ContBuild')
        {
            steps
            {
               sh 'mvn package' 
            }
        }
        stage('ContDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Declarativ1/webapp/target/webapp.war ubuntu@172.31.10.172:/var/lib/tomcat10/webapps/testapp.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh ' java -jar /var/lib/jenkins/workspace/Declarativ1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Declarativ1/webapp/target/webapp.war ubuntu@172.31.3.113:/var/lib/tomcat10/webapps/prodapp.war'
            }
        }
    }
}
