ipipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
        steps
            {
            git 'https://github.com/srilekhk/maven2.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '539a9edd-ccab-4d79-b99e-98f1712c2aad', path: '', url: 'http://172.31.25.124:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContinuosuDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '539a9edd-ccab-4d79-b99e-98f1712c2aad', path: '', url: 'http://172.31.29.221:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
    }
}
