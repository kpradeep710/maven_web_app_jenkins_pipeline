pipeline {
    agent any
    environment {
        GIT_CREDENTIALS_ID = '57fb32e1-78e2-45f8-9f5a-8af2d98a35e0'
        SSH_KEY = '/c/Documents/nani.pem'
        EC2_USER = 'ec2-user'
        EC2_HOST = '65.0.12.242'
    }
    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main',
                git url: 'https://github.com/kpradeep710/maven_web_app_jenkins_pipeline.git', credentialsId: "${GIT_CREDENTIALS_ID}"
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean package'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh '''
                        scp -i ${SSH_KEY} target/01-maven-web-app.war ${EC2_USER}@${EC2_HOST}:/home/ec2-user/
                    '''
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
