pipeline {
    agent any

    tools {
        jdk 'jdk_local'
        maven 'maven_test'
    }

    stages {
        stage('Compile') {
            steps {
                sh 'mvn clean compile -B'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test -B'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package -B'
            }
            }

        stage('Run App') {
            steps {
                // Run the packaged JAR
                sh 'java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App'
            }
        }
    }
}

