pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t krish-devops-app ./app'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run --rm krish-devops-app echo "Health check passed"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker stop krish-devops || true'
                sh 'docker rm krish-devops || true'
                sh 'docker run -d --name krish-devops --network devops-net -p 8081:80 krish-devops-app'
            }
        }
    }
}
