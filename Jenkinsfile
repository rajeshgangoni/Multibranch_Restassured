pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.6/bin"
    }
    stages{
       stage('GetCode added'){
            steps{
                lock('my-unique-resource'){
                  git branch: 'main', url: 'https://github.com/rajeshgangoni/Multibranch_Restassured.git'
                  //sleep 60
                }          
            }
         }        
       stage('Build '){
            steps{
                sh 'mvn clean package'
            }
         }
    }
}  