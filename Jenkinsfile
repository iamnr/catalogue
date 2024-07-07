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

        stage('upload artifact') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '54.80.58.243:8081/',
                    groupId: 'com.roboshop',
                    version: '1.0.1',
                    repository: 'catalogue',
                    credentialsId: 'nexus-auth',
                    artifacts: [
                        [artifactId: 'catalogue',
                        classifier: '',
                        file: 'catalogue.zip',
                        type: 'zip']
                    ]
                )
            }
        }

    }

    post {

        always {
            echo 'deleting files'
            deleteDir()
        }
    }
}