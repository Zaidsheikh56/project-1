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
    }
}
