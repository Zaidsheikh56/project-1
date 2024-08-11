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
                mvn clean install
                '''
            }
        }
    }
}
