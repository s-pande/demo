pipeline {
    agent any

    stages {
        stage('Format') {
            steps {
                sh 'mvn spotless:apply'
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
