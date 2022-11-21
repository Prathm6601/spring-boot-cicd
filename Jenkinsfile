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
            deploy adapters: [tomcat9(credentialsId: 'bbf8c4a1-ea56-41f5-9ea2-3bf71d38343f', path: '', url: 'http://localhost:8081')], contextPath: '/app', war: '**/*.war'              
            }
            
        }
        stage("Deploy on Prod"){
            steps{
                // deploy on container -> plugin
            deploy adapters: [tomcat9(credentialsId: 'bbf8c4a1-ea56-41f5-9ea2-3bf71d38343f', path: '', url: 'http://localhost:8081')], contextPath: '/app', war: '**/*.war'
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
