pipeline {
    agent any
    stages {
        stage('Clean Workspace') {
            echo "workspace clean compelted"
        }
    }
    post {
        success {
            echo "Website files published successfully!"
        }
        failure {
            echo "Deployment failed. Check the console logs for details."
        }
    }
}
