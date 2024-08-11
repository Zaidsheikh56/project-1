pipeline {
    agent any 
    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/Pritam-Khergade/student-ui.git'
            }
        }
        stage('build') {
           steps{
               sh'''
               mvn clean install 
               '''
           }
       }
        stage('docker build') {
            steps {
                apt-get install docker -y
                docker build -t zaidsheikh5656/lastimage:0 .
                docker login -u zaidsheikh5656 -p zaidzimad12345
                docker push zaidsheikh5656/lastimage:0
            }
        }
    }
}
