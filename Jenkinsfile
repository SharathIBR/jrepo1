pipeline {
    agent any
    tools {
        git 'Default'
        }
    options {
        buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '5')
        }
        environment {
            DOCKERHUB_CREDENTIAL = credentials('dockerhubcred')
            }
    stages {
        stage('build') {
            steps {
                sh 'docker build -t navami99/testrepo2:testimg1 .'
            }
        }
        stage('build') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
                sh 'docker push navami99/testrepo2:testimg1 .'
            }
        }
    }
}
