pipeline {

    agent { node {label 'AGENT-1'}}

    stages {

        stage ('Installing Dependencies'){

            steps {
                sh 'npm install'
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

            directoryDel()
        }
    }
}