
pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
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
                deploy adapters: [tomcat9(credentialsId: '9e9589d7-ac63-4280-afeb-7fd49ef59210', path: '', url: 'http://172.31.26.68:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
           steps
            {
                 git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
          
                 sh 'java -jar  /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '9e9589d7-ac63-4280-afeb-7fd49ef59210', path: '', url: 'http://172.31.16.233:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }  
}

