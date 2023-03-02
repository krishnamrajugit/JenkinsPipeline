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
                deploy adapters: [tomcat9(credentialsId: 'TomcatServerAdminCreds', url: 'http://localhost:8081/')], onFailure: false, contextPath: null, war: '**/*.war'
            }
        }
    }
}
