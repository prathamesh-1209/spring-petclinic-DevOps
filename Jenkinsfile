pipeline {
    agent any

    environment {
        // Enforce lightweight JVM options globally for Gradle
        GRADLE_OPTS = "-Dorg.gradle.jvmargs='-Xmx512m -XX:MaxMetaspaceSize=256m' -Dorg.gradle.daemon=false"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build c') {
            steps {
                // -x test skips tests to save build time and memory on t3.micro
                sh './gradlew assemble -x test'
            }
        }
    }

    post {
        always {
            // Clean workspace to keep the 8GB EBS disk from filling up
            cleanWs()
        }
    }
}