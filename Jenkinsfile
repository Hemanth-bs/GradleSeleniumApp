pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
                export PATH=$JAVA_HOME/bin:$PATH
                java -version
                ./gradlew clean build
                '''
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
