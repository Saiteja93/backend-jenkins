pipeline {
    agent {
        label 'agent -1'
    }
    options{
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    environment {
        DEBUG = 'true'
        appVersion = ''
    }
     stages {
        stage('read the version') {
            steps {
                script {
              def jsonText = readFile 'package.json'
              appVersion = packagejson.version
              echo "App version: ${appVersion}"
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo This is a test'
              
            }
        }
        stage('Deploy') {
          
            steps {

                    sh 'echo This is a deploy'
                    //error 'pipeline failed'
                    

            }
        }
    }
    

    post {
        always {
            echo " this section runs always"
        }
        success {
            echo "this section run when pipeline sucecess"
        }
        failure {
            echo "this section runs when pipeline failed"
        }
    }
}
        
