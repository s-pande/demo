pipeline {
    agent {
        docker {
            image 'maven:3.9.7-eclipse-temurin-17-alpine'
            args '-v ${env.WORKSPACE}:/workspace'
            reuseNode true
        }
    }

    environment {
        WORK_DIR = '/workspace'
    }

    stages {

        stage('Format') {
            steps {
                dir("${env.WORK_DIR}") {
                    sh 'working directory is "${env.WORK_DIR}"'
                }
            }
        }
        stage('Build') {
            steps {
                dir("${env.WORK_DIR}") {
                    sh 'mvn clean install -DskipTests'
                }
            }
        }
        stage('Test') {
            steps {
                dir("${env.WORK_DIR}") {
                    sh 'mvn clean test'
                }
            }
        }
    }

    post {
        always {
            echo "This will always run."
        }
        success {
            echo "The build succeeded."
        }
        failure {
            echo "The build failed."
        }
        unstable {
            echo "The build is unstable."
        }
        aborted {
            echo "The build was aborted."
        }
    }
}
