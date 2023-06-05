pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
//                 slackSend channel: 'youtubejenkins', message: 'Job Started'
                
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
//                 deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://192.168.0.118:8080')], contextPath: '/app', war: '**/*.war'
                   deploy adapters: [tomcat9(credentialsId: '7c6191ff-a71f-4610-b4ae-3f46c82e1d63', path: '', url: 'http://http://3.253.21.96:8080/')], contextPath: '/app', war: '**/*.war'
              
            }
         
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            echo "Jenkins as a code project ran successfully!"
             
        }
        failure{
            echo "========pipeline execution failed========"
             
        }
    }
}
