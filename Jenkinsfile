pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.6/bin"
    }
    stages{
       stage('GetCode added'){
            steps{
                git branch: 'main', url: 'https://github.com/rajeshgangoni/Multibranch_Restassured.git'
            }
         }        
       stage('Build the package'){
            steps{
                sh 'mvn clean package'
            }
         }
    }
}  