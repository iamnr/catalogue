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

    }

    post {

        always {
            cleanWs()
        }
    }
}