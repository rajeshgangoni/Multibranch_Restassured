pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.6/bin"
    }
    stages{
       stage('GetCode applied lock'){
            steps{
                lock('my-unique-resource'){
                  git branch: 'main', url: 'https://github.com/rajeshgangoni/Multibranch_Restassured.git'
                  sleep 60
                }          
            }
         }        
       stage('Build the package'){
            steps{
                sh 'mvn clean package'
            }
         }
    }
}  