pipeline {
    
    agent any

    stages {

        stage('Checkout external proj') {
           steps {
             git branch: 'master',
                credentialsId: 'cb067715-9f4b-4f93-93ff-d4fa802a8c71',
                url: 'https://github.com/deeprangaraj/SampleWebApp'
             sh "ls -la"
           }
        }

        //stage ('install') {
        //    steps {
        //      // use the id of the globally configured maven instance
        //      def mvnTool = tool 'Maven_3_6_3'
        //      // execute maven
        //      sh "${mvnTool}/bin/mvn clean install"
        //    }
        //}

        steps {
                withMaven(maven : 'maven_3_6_3') {
                    sh 'mvn clean compile'
                }
        }

    }
}
