pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'gradle clean build'
            }
        }

        stage('Test (Selenium)') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Report') {
            steps {
                junit '**/build/test-results/test/*.xml'
            }
        }
    }

    post {
        success {
            echo 'Build & Selenium tests passed!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
