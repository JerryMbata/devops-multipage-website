pipeline {

agent any


environment {

IMAGE_NAME = "jerrymbata1/home-page"

IMAGE_TAG = "${BUILD_NUMBER}"

}


stages {


stage('Checkout Code') {

steps {

git branch: 'main',
url: 'https://github.com/YOUR_USERNAME/devops-portal.git'

}

}



stage('Build Docker Image') {

steps {

sh """

docker build \
-t ${IMAGE_NAME}:${IMAGE_TAG} \
./home

"""

}

}



stage('Docker Login') {

steps {

withCredentials([usernamePassword(
credentialsId: 'dockerhub',
usernameVariable: 'USERNAME',
passwordVariable: 'PASSWORD'
)]) {


sh """

echo $PASSWORD | docker login \
-u $USERNAME \
--password-stdin

"""

}

}

}



stage('Push Image') {

steps {

sh """

docker push ${IMAGE_NAME}:${IMAGE_TAG}

"""

}

}



stage('Deploy To Kubernetes') {

steps {

sh """

kubectl set image deployment/home \
home=${IMAGE_NAME}:${IMAGE_TAG}

"""

}

}


}

}
