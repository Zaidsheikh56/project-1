pipeline {
    agent any 
    stages {
        stage('git checkout') {
            steps {
                sh 'sudo apt install git -y'
                git 'https://github.com/Pritam-Khergade/student-ui.git'
            }
        }
    }
}
