pipeline{
    agent any
    environment {
        PATH = "$PATH:/C:/Program Files/apache-maven-3.9.3-bin/apache-maven-3.9.3/bin"
    }
 stages {
        stage('clone repo') {
            steps {
                git branch: 'main',
                url: 'https://github.com/kpradeep710/maven_web_app_jenkins_pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo "build the maven project"
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                echo "connected to ec2-instance and ready to deploy"
                sh '''
                ssh -i C:/Documents/nani.pem target/01-maven-web-app.war ec2-user@65.0.12.242:/home/ec2-user/
                '''
            }
        }
    }
}
