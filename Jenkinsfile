pipeline{
    agent any
    tools{
        maven 'Installed_Maven'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    archiveArtifacts artifacts: '**/target/*.war', followSymlinks: false
                }
            }
        }
        stage('Deploy'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'TomcatCredentials', path: '', url: 'http://localhost:8081/')], contextPath: 'WebApp', war: '**/*.war'
            }
        }
    }
}