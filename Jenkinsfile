pipeline {
    agent any

    stages {
        stage('Greeting') {
            steps {
                sh 'sudo yum update -y'
                sh 'sudo yum install git -y'
                git 'https://github.com/Pritam-Khergade/student-ui.git'
                
            }
        }
      
        stage('Build-stage') {
            steps {
                sh'''
                sudo yum update -y && sudo yum install maven -y
                sudo cd /var/lib/jenkins/workspace/zaid && mvn clean install
                '''
            }
        }
        stage('deploy-stage') {
            steps {
               deploy adapters: [tomcat9(credentialsId: '44dc28fc-72de-431a-a681-69d18af1618e', path: '', url: 'http://172.31.3.203:8080/')], contextPath: '/', war: '**/*.war' 
            }
        }
       
    }
}
