pipeline {
    agent any 
    stages {
        stage('git checkout') {
            steps {
                sh 'yum install git -y'
                git 'https://github.com/Pritam-Khergade/student-ui.git'
            }
        }
    }
}
