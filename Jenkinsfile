pipeline {
    agent any

    // Define environment variables used across the pipeline
    environment {
        APP_NAME = 'my-awesome-app'
        DOCKER_REGISTRY = 'registry.example.com'
    }

     // Keep only the last 5 builds to save disk space
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
        timeout(time: 1, unit: 'HOURS')
        //ansiColor('xterm')
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Example for a Maven project
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
            post {
                always {
                    // Publish test results to Jenkins
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Dockerize & Push') {
            steps {
                echo 'Building and pushing Docker image...'
                // Example of using credentials safely
                // withCredentials([string(credentialsId: 'docker-hub-secret', variable: 'TOKEN')]) {
                //     sh "docker login -u myuser -p ${TOKEN}"
                //     sh "docker build -t ${DOCKER_REGISTRY}/${APP_NAME}:${env.BUILD_NUMBER} ."
                //     sh "docker push ${DOCKER_REGISTRY}/${APP_NAME}:${env.BUILD_NUMBER}"
                // }
                sh 'echo "Docker build skipped for this sample."'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
            // slackSend channel: '#deployments', message: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' completed successfully."
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
            // slackSend channel: '#deployments', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed."
        }
        always {
            cleanWs() // Clean up the workspace after the build finishes
        }
    }
}
