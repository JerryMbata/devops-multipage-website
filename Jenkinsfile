pipeline {

    agent any

    environment {

        IMAGE_NAME = "jerrymbata1/home-page"
        IMAGE_TAG = "${BUILD_NUMBER}"

    }


    stages {


        stage('Build Docker Image') {

            steps {

                echo "Building Docker image..."

                sh """
                docker build \
                -t ${IMAGE_NAME}:${IMAGE_TAG} \
                ./home
                """

            }

        }



        stage('Docker Login') {

            steps {

                echo "Logging into Docker Hub..."

                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub',
                        usernameVariable: 'DOCKER_USER',
                        passwordVariable: 'DOCKER_PASS'
                    )
                ]) {

                    sh """

                    echo \$DOCKER_PASS | docker login \
                    -u \$DOCKER_USER \
                    --password-stdin

                    """

                }

            }

        }



        stage('Push Docker Image') {

            steps {

                echo "Pushing image to Docker Hub..."

                sh """

                docker push ${IMAGE_NAME}:${IMAGE_TAG}

                """

            }

        }



        stage('Deploy To Kubernetes') {

            steps {

                echo "Deploying to Kubernetes..."

                sh """

                kubectl set image deployment/home \
                home=${IMAGE_NAME}:${IMAGE_TAG}

                """

            }

        }



        stage('Verify Deployment') {

            steps {

                echo "Checking rollout status..."

                sh """

                kubectl rollout status deployment/home

                kubectl get pods

                """

            }

        }


    }


    post {

        success {

            echo "Deployment completed successfully!"

        }


        failure {

            echo "Deployment failed. Check logs."

        }

    }


}
