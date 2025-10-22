pipeline {
  agent any
  environment {
    IMAGE_NAME = "jenkins-pipeline-app"
    IMAGE_TAG = "latest"
  }
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/BhaveshJangale/jenkins-ci-cd-pipeline.git'
      }
    }
    stage('Build') {
      steps {
        echo 'Building Docker image...'
        sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
      }
    }
    stage('Test') {
      steps {
        echo 'Running tests (placeholder)...'
        sh 'docker run --rm $IMAGE_NAME:$IMAGE_TAG npm test || true'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying container...'
        sh 'docker run -d --name $IMAGE_NAME -p 3000:3000 $IMAGE_NAME:$IMAGE_TAG || true'
      }
    }
  }
  post {
    success { echo '✅ Pipeline completed successfully!' }
    failure { echo '❌ Pipeline failed!' }
  }
}
