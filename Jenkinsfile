pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            when {
                branch 'master'
            }
            steps {
                echo 'Building on master branch'
                // Add your build steps here, e.g., compiling code, running build scripts, etc.
            }
        }

        stage('Test') {
            when {
                branch 'develop'
            }
            steps {
                echo 'Running tests on develop branch'
                // Add your test steps here, e.g., running unit tests, integration tests, etc.
            }
        }

        stage('Feature Branch') {
            when {
                branch pattern: "feature/.*", comparator: "REGEXP"
            }
            steps {
                echo 'Running on a feature branch'
                // Add your steps for feature branches here, e.g., static analysis, additional testing, etc.
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add cleanup steps here if needed
        }
        success {
            echo 'Build succeeded!'
            // Add steps for successful builds, e.g., notifications
        }
        failure {
            echo 'Build failed!'
            // Add steps for failed builds, e.g., notifications
        }
    }
}
