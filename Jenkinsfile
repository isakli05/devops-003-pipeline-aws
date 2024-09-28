pipeline {
    agent any
    
    tools{
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }
        
        stage('Checkout From SCM') {
            steps {
                //checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/isakli05/devops-003-pipeline-aws']])
                git branch :'master', credentialsId: 'github', url: 'https://github.com/isakli05/devops-003-pipeline-aws'
            }
        }
        
        stage('Build Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Test Application') {
            steps {
                  sh 'mvn test'
            }
        }
    }
}
