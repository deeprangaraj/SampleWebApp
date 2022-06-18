pipeline {
    agent any

    stages {
        stage ('Compile') {

            steps {
                withMaven(maven : 'maven_3_8_4') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Build') {

            steps {
                withMaven(maven : 'maven_3_8_4') {
                    sh 'mvn init'
                }
            }
        }

    }
}
