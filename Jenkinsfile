pipeline {
    agent any

    stages {
        stage('Cleanup') {
            steps {
                sh 'docker stop my-website || true'
                sh 'docker rm my-website || true'
            }
        }
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Vjuser/Jenkins_Repo.git', branch: 'main'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t simple-web-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d --name my-website -p 8081:80 simple-web-app'
            }
        }
    }
}
