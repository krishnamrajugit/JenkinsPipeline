pipeline{
    agent any
    tools{
        maven 'Local_Maven'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Deploy'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'TomcatServerAdminCreds', path: '', url: 'http://localhost:8081/')], contextPath: 'CICDWebApp', war: '**/*.war'
            }
        }
    }
}
