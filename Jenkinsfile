pipeline {
    agent any

    environment {
        // Define any environment variables if needed
        DOCKER_IMAGE = 'demo-app-mosheliya:${BUILD_NUMBER}'
    }

    stages {
        stage('Build') {
            steps {
                // Build with Maven
                script {
                    withMaven(maven: 'M3') {
                        sh 'mvn clean package'
                    }
                }
            }
        }

        stage('Dockerize') {
            steps {
                script {
                    // Building Docker Image
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    // Assuming Docker Hub, replace with your registry
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-credentials-id') {
                        docker.image(DOCKER_IMAGE).push()
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Deploy to Kubernetes
                    kubernetesDeploy(
                        configs: 'k8s-deployment.yml',
                        kubeconfigId: 'YOUR_KUBECONFIG_ID'
                    )
                }
            }
        }
    }

    post {
        always {
            // Clean up Docker Images
            sh "docker rmi ${DOCKER_IMAGE}"
        }
    }
}
