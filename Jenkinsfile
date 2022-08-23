pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.6/bin"
    }
    stages{
        stage("Git clone"){
            steps{
                git branch: 'main', url: 'https://github.com/rajeshgangoni/Multibranch_Restassured.git'
            }
        }
        stage("Test"){
            steps{
                sh 'mvn test'
            }
        }
        // stage("Publish html reports"){
        //     steps{
        //         publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'test-output', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
        //     }
        // }
        
    }
    // post{
    //     always {
    //       junit 'test-output/junitreports/*.xml'
    //     }
    // }
    post {
        success {
          // publish html
          publishHTML target: [
              allowMissing: false,
              alwaysLinkToLastBuild: false,
              keepAll: true,
              reportDir: 'test-output',
              reportFiles: 'index.html',
              reportName: 'RCov Report'
            ]
        }
      }
}