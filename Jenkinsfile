pipeline {
    agent any
    
    stages {
        stage('Checkout Code'){
            steps {
                git url: 'https://github.com/swap1408/Devops.git', branch:'main'
            }
        }
        
        stage('Install Dependencies'){
            steps {
                sh 'npm install'
            }
        }
        
        stage('Run Unit Tests'){
            steps {
                sh 'npm test'
            }
        }
        
        stage('Build artifact'){
            steps {
                sh 'zip -r build.zip .'
            }
        }
        
        stage('Archive Artifact'){
            steps {
              archiveArtifacts artifacts: 'build.zip', fingerprint:true
            }
        }
        
        stage('Notifications'){
            steps {
                echo 'Build and tests succeeded!'
            }
        }
    }
    
    post {
        failure {
            echo 'Build failed. Please check logs'
        }
    }
}
