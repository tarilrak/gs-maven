pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                git branch: 'main',
                    
                    url: env.GIT_URL
            }
        }
        
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
            post {
                success {
                    // If build succeeds, archive the build artifacts
                    archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
                }
                failure {
                    // If build fails, send a notification or take other actions
                    echo 'Build failed! Please check the build logs.'
                }
            }
        }
    }
    
    // Post-build actions (optional)
    post {
        always {
            // Clean up workspace after the build is complete
            cleanWs()
        }
    }
}
