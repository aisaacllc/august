pipeline {
    agent any
    stages {
        stage('Clean Workspace') {
            echo "workspace clean compelted"
        }
    stage('Checkout Source') 
            {
              echo "Checkout complete!"
            }
        
    stage('Publish Website Files') {
            steps {
                      echo "Publish complete!"
            }
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
