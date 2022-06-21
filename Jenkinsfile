pipeline {
    
    agent { label 'java-docker-agent' }

    tools {
       maven '3.8.6'
    }
 
    stages {

        stage('Checkout external proj') {
           steps {
             git branch: 'master',
                credentialsId: 'cb067715-9f4b-4f93-93ff-d4fa802a8c71',
                url: 'https://github.com/deeprangaraj/SampleWebApp'
             sh "ls -la"
           }
        }

        stage ('maven version') {
            steps {
                sh 'mvn --version'
            }
        }

        stage('maven compile') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('docker build') {
           steps {

               sh 'docker build -t deeprangaraj/sample-app:1.0 .'

           }

        }
    }
}
