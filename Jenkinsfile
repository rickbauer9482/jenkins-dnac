pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '10')) // Retain history on the last 10 builds
        timestamps() // Append timestamps to each line
        timeout(time: 20, unit: 'MINUTES') // Set a timeout on the total execution time of the job
    }
    agent {
        dockerNode { 
            image 'python:latest' 
        }
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
                    sh 'pip install -r requirements.txt'
                    // echo 'Deploying configuration templates....'
                    // sh "python cli_templates.py"
                }
            }
        }
    }
}
