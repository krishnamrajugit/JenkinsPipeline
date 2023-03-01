pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Deploy'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'TomcatCredentials', path: '', url: 'http://localhost:8081/')], contextPath: 'CICDWebApp', war: 'target/*.war'
            }
        }
    }
}
