node('built-in') 
{
    stage('Continuous Download') 
    {
       git 'https://github.com/intelliqittrainings/maven.git' 
    }
    
    stage('Continuous Build') 
    {
       sh 'mvn package'
    }
    
    stage('Continuous Deployment') 
    {
       deploy adapters: [tomcat9(credentialsId: 'bd09c46d-37e3-401e-bafe-9bae10fa68bd', path: '', url: 'http://172.31.9.31:8080')], contextPath: 'test app', war: '**/*.war'
    }
    
    stage('Continuous Testing') 
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /root/.jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    
    stage('Continuous Delivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'bd09c46d-37e3-401e-bafe-9bae10fa68bd', path: '', url: 'http://172.31.13.209:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}



