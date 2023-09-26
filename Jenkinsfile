pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '10')) // Retain history on the last 10 builds
        timestamps() // Append timestamps to each line
        timeout(time: 20, unit: 'MINUTES') // Set a timeout on the total execution time of the job
    }
    agent any 
    stages {
        stage('Build Docker') {
            agent {
                dockerContainer {
                    image 'python:latest'
                    reuseNode true
                }
            }
        }

    }
    steps {
        sh 'python --version'
    }
  post {
    cleanup {
      cleanWs()
    }
  }
}
