pipeline{
    agent any
    tools{
        maven 'Local_Maven'
    }
    stages{
        stage('Build'){
                sh 'mvn clean install'
        }
        stage('Archive Artifacts'){
                archiveArtifacts artifacts: 'target/*.war'   
        }
        stage('Deploy'){
                deploy adapters: [tomcat9(credentialsId: 'TomcatServerAdminCreds', url: 'http://localhost:8081/')], onFailure: false, contextPath: null, war: 'target/*.war'
        }
    }
}
