pipeline {

    agent { node {label 'agent-1'}}

    stages {

        stage ('Installing Dependencies'){

            steps {
                echo 'Dependencies installed'
            }
        }

        stage ('unit test'){
            
            steps {
                echo 'unit testing is done here'
            }
        }

        stage('Build') {
            steps {
              sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'  
            }
        }

    }

    post {

        always('deleting files') {
            deleteDir()
        }
    }
}