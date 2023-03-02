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
    }
}
