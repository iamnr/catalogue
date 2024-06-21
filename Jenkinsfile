pipeline {

    agent { node {label 'AGENT-1'}}

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
    }

    post {

        always {

            echo 'cleaning up directory'
            deleteDir()
        }
    }
}