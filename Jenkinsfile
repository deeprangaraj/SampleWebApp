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

        stage ('Build') {

            steps {
                withMaven(maven : 'maven_3_11_0') {
                    sh 'mvn init'
                }
            }
        }

    }
}
