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


        stage ('zipping files'){

            steps {

                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'
            }
        }
    }

    // post {

    //     always {

    //         cleanWs(
    //             deleteDirs:true
    //         )

    //     }
    // }
}