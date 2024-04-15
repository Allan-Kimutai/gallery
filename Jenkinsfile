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
        
        stage('Run Tests') {
            steps {
                // Run npm test command
                sh 'npm test'
            }
        }
        
        stage('Deploy to Render') {
            steps {
                // Deploy to Render
                sh 'curl -X POST -d "" https://api.render.com/deploy/srv-codc2mol6cac73bh8pog?key=ypSaKJTo8Cw'
            }
        }
        
        stage('Send slack Message') {
            steps {
                // Send slack message when deployment is successful
                slackSend color: 'good', message: 'Deployment successful. Build ID: dccfc49, Link to Render - https://gallery-qlmc.onrender.com/'
            }
        }
    }
}
