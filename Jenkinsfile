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
        stage('Archive Artifacts'){
            steps{
                   archiveArtifacts artifacts: 'target/*.war'   
            }   
        }
        stage('Deploy'){
            steps{
                   deploy adapters: [tomcat9(credentialsId: 'TomcatServerAdminCreds', url: 'http://localhost:9050/')], onFailure: false, contextPath: null, war: 'target/*.war'
            }
        }
    }
}
