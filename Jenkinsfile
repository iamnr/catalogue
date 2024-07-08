pipeline {

    agent { node {label 'agent-1'}}

    environment {
        packageVersion = ''
    }

    stages {

        stage ('get version') {
            steps {
                script{
                    def packageJson = readJSON(file: 'package.json')
                    packageVersion = packageJson.version
                    echo "${packageVersion}"
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
            }
        }

        stage('Build') {
            steps {
              sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip' 
              echo "${packageVersion}" 
            }
        }

        stage('upload artifact') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '54.90.119.154:8081/',
                    groupId: 'com.roboshop',
                    version: "$packageVersion",
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

        stage('calling downstream job') {
            steps {
                script {

                    def params = [
                        string(name: 'version' , value: "$packageVersion")
                    ]
                    build job: "../catalogue-deploy" , wait: true , parameters: params
                }
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