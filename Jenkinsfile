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
        stage('Read the version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "App version: ${appVersion}"
                }
            }
        }
        stage('install dependencies') {
            steps {
                sh 'npm install'
                
              
            }
        }
        stage('Docker build') {
          
            steps {

                    sh """
                    docker build -t joindevops/backend:${appVersion} .
                    docker images
                    """      

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
        
