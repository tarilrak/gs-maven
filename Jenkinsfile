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
