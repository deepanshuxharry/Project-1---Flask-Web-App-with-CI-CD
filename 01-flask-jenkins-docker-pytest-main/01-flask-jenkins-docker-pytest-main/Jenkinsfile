pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flaskapp-autodeployer:latest'
        CONTAINER_NAME = 'flaskapp'
        CONT_PORT = '5000'
        HOST_PORT = '5000'
    }

    stages {

        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Clone Repository') {
            steps {
                echo "Cloning Git repository..."
                git branch: 'main', url: 'https://github.com/Sayantan2k24/01-flask-jenkins-docker-pytest.git'
            }
        }

        stage('Install pip') {
            steps {
                echo "Installing pip..."
                sh 'sudo yum install -y python3-pip'
            }
        }

        stage('Install Python Dependencies') {
            steps {
                echo "Installing Python dependencies..."
                sh 'pip3 install --user -r requirements.txt'
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo "Running unit tests..."
                sh 'export PATH=$PATH:$HOME/.local/bin && pytest'
            }
        }

        stage('Clean Old Docker Resources') {
            steps {
                echo "Stopping and removing existing Docker container if any..."
                sh """
                    docker stop $CONTAINER_NAME || true
                    docker rm $CONTAINER_NAME || true
                """
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh "docker build --no-cache -t $IMAGE_NAME ."
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "Running Docker container..."
                sh "docker run -d -p $HOST_PORT:$CONT_PORT --name $CONTAINER_NAME $IMAGE_NAME"
            }
        }
    }

    post {
        success {
            echo '✅ Flask App Deployed Locally via Docker!'
        }
        failure {
            echo '❌ Build/Deployment Failed. Check Console Output.'
        }
    }
}
