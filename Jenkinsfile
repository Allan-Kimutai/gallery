pipeline {
    agent any
    
    tools {
        // Define Node.js tool installation.
        nodejs 'NodeJS'
    }
    
    stages {
        stage('Clone Code') {
            steps {
                // Trigger the pipeline automatically on new changes
                git branch: 'master', url: 'https://github.com/Allan-Kimutai/gallery.git'
                
                // Install required software and dependencies
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                // Run the build command specified in Jenkinsfile
                sh 'npm run'
            }
        }
        
        stage('Deploy to Render') {
            steps {
                // Deploy to Render
                sh 'node server &'
            }
        }
    }
}
