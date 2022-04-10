pipeline{
    agent{
        label 'worker'
    }
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
                sshagent(['tomtom']) {
                sh "scp -o StrictHostKeyChecking=no target/onlinebookstore-0.0.1-SNAPSHOT.war ec2-user@http://3.108.193.253/opt/tomcat/webapps/"
}
            }
        }
}
}
