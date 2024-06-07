pipeline {
        agent {
        docker {
            image 'maven:3.9.7-eclipse-temurin-17-alpine'
            args '-v ${env.WORKSPACE}:/workspace'
            reuseNode true
        }
    }

    stages {
        stage('Format') {
            steps {
                sh 'echo start of pipeline!'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn clean test'
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
