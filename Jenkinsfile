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
                  deploy adapters: [tomcat9(credentialsId: 'TomcatServerAdminCreds', path: '', url: 'http://localhost:9050/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}
