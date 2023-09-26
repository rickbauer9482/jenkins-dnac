pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '10')) // Retain history on the last 10 builds
        timestamps() // Append timestamps to each line
        timeout(time: 20, unit: 'MINUTES') // Set a timeout on the total execution time of the job
    }
    agent {
        docker { 
            // dockerHost 'tcp://172.30.1.180:4243'
            image 'python:latest' 
            }
    }
    environment {
        JENKINS_REPO_NAME = 'jenkins_dnac'
    }

    stages {
        stage('Checkout'){
           steps {
            checkout scm
           }
        }
        stage('Test') {
            steps {
                sh 'python --version' 
            }
        }
        stage('CLI Templates') {
            steps {
                withEnv(["HOME=${env.WORKSPACE}"]) {
                    sh 'pip install -r requirements.txt --no-warn-script-location'
                    echo('\n\nVerify Python version and Libraries:..............................')
                    sh 'python --version'
                    sh 'pip3 list'
                    echo('\n\nVerify Application Files:..............................')
                    sh 'ls -la'
                }
            }
        }
    }
}
