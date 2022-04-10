pipeline{
    agent any
    tools
    {
        maven 'maven3.6.3'
    }
    stages{
        stage("CheckOutCode")
        {
            steps{
                git branch: 'J2EE', credentialsId: 'd7b024f9-b67e-40a7-ac64-faa4651da08b', url: 'https://github.com/pracforme/onlinebookstore.git'
            }
        }
        stage("Build")
        {
        steps{
            sh "mvn clean package"
        }
        }
        stage("DeployInTomcat")
        {
            steps{
                sshagent(['72873b8d-60ae-4f8a-8f2c-9dacb5196c46']) {
                sh "scp -o StrictHostKeyChecking=no target/onlinebookstore-0.0.1-SNAPSHOT.war ec2-user@http://3.108.193.253/opt/tomcat/webapps/"
}
            }
        }
}
}
