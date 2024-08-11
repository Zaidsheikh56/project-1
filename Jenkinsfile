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
        stage('code-quality') {
            steps{
                sh'''
                sudo yum install docker -y
                sudo systemctl start docker
                sudo docker pull sonarqube
                sudo docker network create sonar-network1
                sudo docker run -d --name sonar-db1 --network sonar-network1 -e POSTGRES_USER=sonar -e POSTGRES_PASSWORD=sonar -e POSTGRES_DB=sonar postgres:9.6
                sudo docker run -d --name sonar1 -p 9000:9000 --network sonar-network1 -e SONARQUBE_JDBC_URL=jdbc:postgresql://sonar-db:5432/sonar -e SONAR_JDBC_USERNAME=sonar -e SONAR_JDBC_PASSWORD=sonar sonarqube
                mvn sonar:sonar  -Dsonar.host.url=http://172.31.26.49:9090 -Dsonar.login=squ_b3598f14e7ddeb17698d8b91f9842974c84da3e7
                '''
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
        stage('deploy-stage') {
            steps {
               deploy adapters: [tomcat9(credentialsId: '44dc28fc-72de-431a-a681-69d18af1618e', path: '', url: 'http://172.31.3.203:8080/')], contextPath: '/', war: '**/*.war' 
            }
        }
       
    }
}
