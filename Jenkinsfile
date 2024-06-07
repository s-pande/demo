pipeline {
      agent any

    stages {
        stage('Format') {
            steps {
               bat 'echo start of pipeline!'
            }
        }
        stage('Build') {
            steps {
               bat 'mvn clean install -DskipTests'
            }
        }
        stage('Test') {
            steps {
               bat 'mvn clean test'
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
