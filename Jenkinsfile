pipeline {
    agent any
     tools {
        maven 'maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
            deploy adapters: [tomcat9(credentialsId: 'bf92eaee-19d7-4259-a3f7-5e10d8b7fc3a', path: '', url: 'http://52.90.221.109:8080')], contextPath: '/app', war: '**/*.war'              
            }
            
        }
        stage("Deploy on Prod"){
            steps{
                // deploy on container -> plugin
            deploy adapters: [tomcat9(credentialsId: 'b16d657d-5429-4056-a6bb-31e5791bc2e0', path: '', url: 'http://54.234.38.235:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
