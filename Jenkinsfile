pipeline{
    agent any
    environment {
        PATH = "$PATH:/C:/Program Files/apache-maven-3.9.3-bin/apache-maven-3.9.3/bin"
    }
    stages{
       stage('GetCode'){
            steps{
				git branch: 'main',
                url: 'https://github.com/kpradeep710/maven_web_app_jenkins_pipeline.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }       
    }
}
