pipeline {

    agent { node {label 'agent-1'}}

    environment {
        packageVersion = ''
    }

    stages {

        stage ('version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    def packageVersion = packageJson.version
                    echo "${packageJson.version}"
                }
            }
        }

        stage ('Installing Dependencies'){

            steps {
                echo 'Dependencies installed'
            }
        }

        stage ('unit test'){
            
            steps {
                echo 'unit testing is done here'
                echo '${packageVersion}'
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
                    nexusUrl: '54.90.119.154:8081/',
                    groupId: 'com.roboshop',
                    version: '$packageVersion',
                    repository: 'catalogue',
                    credentialsId: 'nexus',
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