pipeline {
    
    agent { label 'jenkins-worker' }

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

        stage('maven install') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('docker build') {

           steps {
               sh 'docker build -t deepapraj/sample-app:2.0 .'
           }
        }

        stage('Push Docker Image') {

            steps {
                withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
                   sh "docker login -u deepapraj -p ${dockerHubPwd}"
                }
                sh 'docker push deepapraj/sample-app:2.0'
            }
        }

        //stage('Run Container on Dev Server') {
        //    def dockerRun = 'docker run -p 8080:8080 -d --name sample-app deepapraj/sample-app:2.0'
        //    sshagent(['dev-server']) {
        //        sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.18.198 ${dockerRun}"
        //    }
        //}
    }
}
