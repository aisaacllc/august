pipeline {
    agent any
    }
    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout Source') {
            steps {
                script {
                    //git branch: "${params.BRANCH}",
                    //credentialsId: 'Jenkins-CI-Token',
                    //url: "${params.REPO_URL}"
                }
            }
        }
                      stage('Publish Website Files') {
    steps {
                        echo "Success"
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
