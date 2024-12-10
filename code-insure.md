````
pipeline {
    agent any
    tools {
        maven 'ap-maven'
    }


    stages{
        stage("Code-Pull"){
        steps{
            git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/abhipraydhoble/Project-InsureMe.git'
           }
        }
        
        stage("Code-Build"){
            steps{
                sh 'mvn clean package'
            }
        }
        
         stage("Containerize"){
            steps { 
               sh "docker build -t abhipraydh96/dev-b41 ."
            }
        }
        
        stage("Code-Push"){
            steps{
              withCredentials([usernamePassword(credentialsId: 'docker-cred', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
            	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                sh 'docker push abhipraydh96/dev-b41'  
               }
           }
       }
       
       stage("Code-Deploy"){
           steps {
               sh ' docker run -itd -p 8089:8081 abhipraydh96/dev-b41 '
           }
       }
       
    }
}
