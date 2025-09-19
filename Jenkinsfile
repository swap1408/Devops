pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        git url: 'https://github.com/swap1408/Devops.git'
      }
    }

    stages('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stages('Run Unit Tests') {
      steps {
        sh 'npm test'
      }
    }

    stages('Build artifact') {
      steps {
        sh 'zip -r build.zip.'
      }
    }

    stages('Archive Artifact') {
      steps {
        archiveArtifacts artifacts: 'build.zip', fingerprint: true
      }
    }

    stages('Notifications') {
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
