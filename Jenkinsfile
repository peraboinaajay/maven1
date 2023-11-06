node('built-in')
{
    
    stage('download git')
    {
    git 'https://github.com/peraboinaajay/maven1.git'
    
    }
    stage('continuous build') 
    {
     sh 'mvn package'
    }
    stage('continuous deploy') 
    {
        
     deploy adapters: [tomcat9(credentialsId: '2ab10c86-a393-4cf6-8cbd-217345dea845', path: '', url: 'http://172.31.44.255:8080')], contextPath: 'test', war: '**/*.war'  
    }
    
     stage('continuous testing') 
    {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
     sh  'java -jar /var/lib/jenkins/workspace/scripting/testing.jar'
    }
    
    stage('continuous delivery') {
    input message: 'waiting for approve ', submitterParameter: 'ajju'
    deploy adapters: [tomcat9(credentialsId: '2ab10c86-a393-4cf6-8cbd-217345dea845', path: '', url: 'http://13.232.209.115:8080/')], contextPath: 'prod', war: '**/*.war'
    }
    
    
    
    
}