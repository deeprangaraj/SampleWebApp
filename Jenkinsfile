pipeline {
    agent any

    stages {
        stage ('Compile') {

            steps {
                withMaven(maven : 'maven_3_11_0') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('compile') {
            steps {
                // use the id of the globally configured maven instance
                def mvnTool = tool 'Maven_3_6_3'

                // execute maven
                sh "${mvnTool}/bin/mvn clean compile"
            }
        }

        stage ('install') {
            steps {
                // use the id of the globally configured maven instance
                def mvnTool = tool 'Maven_3_6_3'
             
                // execute maven
                sh "${mvnTool}/bin/mvn clean install"
            }
        }

    }
}
