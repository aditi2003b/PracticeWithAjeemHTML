pipeline{
  agent any

  environment{
    IMAGE_NAME = 'PracticeAJ'
    CONTAINER_NAME = 'PracticeAJAD'
  }

  stages{
    stage('Clone'){
      steps{
        git branch: 'main', url: 'https://github.com/aditi2003b/PracticeWithAjeemHTML'
      }
    }
    stage('Build'){
      steps{
        script{
          sh "docker build -t $IMAGE_NAME ."
        }
      }
    }
    stage('Run'){
      steps{
        script{
          sh "docker rm -f $CONTAINER_NAME || true"

          sh "docker run -dit --name $CONTAINER_NAME -p 8089:80 $IMAGE_NAME"
        }
      }
    }
  }
  post{
    success{
      echo "Done Jenkins"
    }
    failure{
      echo "Not Done Jenkins"
    }
  }
