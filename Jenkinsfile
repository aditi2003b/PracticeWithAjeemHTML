pipeline {
  agent any

  environment {
    IMAGE_NAME = 'PracticeAJ'
    CONTAINER_NAME = 'PracticeAJAD'
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/aditi2003b/PracticeWithAjeemHTML'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          sh "docker build -t $IMAGE_NAME ."
        }
      }
    }

    stage('Run Container') {
      steps {
        script {
          // Stop and remove old container if it exists
          sh "docker rm -f $CONTAINER_NAME || true"

          // Run new container on port 8089 mapped to container's 80
          sh "docker run -dit --name $CONTAINER_NAME -p 8089:80 $IMAGE_NAME"
        }
      }
    }
  }

  post {
    success {
      echo "✅ Deployment Successful: App running on port 8089"
    }
    failure {
      echo "❌ Deployment Failed: Check Jenkins logs"
    }
  }
}
