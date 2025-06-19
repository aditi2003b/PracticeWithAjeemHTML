pipeline {
  agent any

  environment {
    IMAGE_NAME = 'practiceaj'        // ✅ lowercase
    CONTAINER_NAME = 'practiceajad'  // ✅ lowercase
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
          sh "docker rm -f $CONTAINER_NAME || true"
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
