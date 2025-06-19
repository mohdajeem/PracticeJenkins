pipeline{
  agent any

  environment{
    IMAGE_NAME = "static_html_page"
    CONTAINER_NAME = "static_html_container"
  }

  stages{
    stage("Clone"){
      steps{
        git branch: "main", url:'https://github.com/mohdajeem/PracticeJenkins.git'
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
          sh "docker rm $CONTAINER_NAME || true"
          sh "docker run -itd --name $CONTAINER_NAME -p 8089:80 $IMAGE_NAME"
        }
      }
    }
    post{
      success{
        echo "done"
      }
      failure{
        echo "Error"
      }
    }
  }
}
