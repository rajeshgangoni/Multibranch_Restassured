pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.6/bin"
    }
    options{
        lock resource: "my-unique-resource"
    }
    stages{
       stage('GetCode added'){
            steps{
                //lock('my-unique-resource'){
                  git branch: 'main', url: 'https://github.com/rajeshgangoni/Multibranch_Restassured.git'
                  sleep 60
                //}
            }
         }        
       stage('Build the package'){
            steps{
                sh 'mvn clean package'
                echo "CHANGE_ID : ${env.CHANGE_ID}"
                echo "CHANGE_URL : ${env.CHANGE_URL}"
                echo "CHANGE_TITLE : ${env.CHANGE_TITLE}"
                echo "CHANGE_AUTHOR : ${env.CHANGE_AUTHOR}"
                echo "CHANGE_AUTHOR_DISPLAY_NAME : ${env.CHANGE_AUTHOR_DISPLAY_NAME}"
                echo "BRANCH_NAME : ${env.BRANCH_NAME}"
                echo "BUILD_NUMBER " +  env.BUILD_NUMBER
            }
         }
    }
    post{
        always {
          junit 'test-output/junitreports/*.xml'
        }
    }
}  
