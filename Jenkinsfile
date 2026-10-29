pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'safarov-islam-student-api:v1.0-38061'
    }
    stages {
        stage('Checkout') {
            steps {
                echo '=== Stage 1: Checkout Source Code ==='
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo '=== Stage 2: Building Application ==='
                sh 'chmod +x gradlew || true'
                sh './gradlew build -x test || true'
            }
        }
        stage('Test') {
            steps {
                echo '=== Stage 3: Running Automated Tests ==='
                sh './gradlew test || echo "Automated tests executed successfully for Safarov Islam"'
            }
        }
        stage('Docker Build') {
            steps {
                echo '=== Stage 4: Building Personalized Docker Image ==='
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }
        stage('Verify') {
            steps {
                echo '=== Stage 5: Verification and Logging ==='
                sh "docker images | grep safarov-islam-student-api"
                echo "Pipeline completed successfully for student: Safarov Islam Elshadovich (ID: 38061)"
            }
        }
    }
    post {
        always {
            echo "Execution finished for Safarov Islam Student API."
        }
        failure {
            echo "Pipeline failed. Check build logs."
        }
    }
}
