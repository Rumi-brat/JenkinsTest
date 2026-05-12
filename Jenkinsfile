pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                // Jenkins automatically checks out the code for Multibranch Pipeline
                // You don't need a manual git step here!
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building HTML project...'
                // For HTML, we just verify the file exists
                script {
                    if (fileExists('index.html')) {
                        echo '✅ index.html found!'
                    } else {
                        error '❌ index.html not found!'
                    }
                }
            }
        }
        
        stage('Publish HTML') {
            steps {
                // This publishes the HTML so you can view it in Jenkins
                publishHTML (target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: '.',
                    reportFiles: 'index.html',
                    reportName: 'My Webpage'
                ])
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
