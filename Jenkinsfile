pipeline {
    agent none
    environment {
        dockerhub=credentials('Docker_Hub')
    }
    stages {
        stage('Build Node App in container') {
            agent { label 'container' }
            steps {
               sh 'echo Building..'
               sh 'docker build -t app .'
               sh 'docker tag app mohamedalaaelsafy/iti-lab1:v1'
               sh 'docker push mohamedalaaelsafy/iti-lab1:v1'
                
            }
        }
        stage('Build Node App in instance') {
            agent { label 'container' }
            steps {
               sh 'echo Building..'
               sh 'docker build -t app .'
               sh 'docker tag app mohamedalaaelsafy/iti-lab1:v1'
               sh 'docker push mohamedalaaelsafy/iti-lab1:v1'
            }
        }
    }

    post {
        success {
            echo 'This will run only if successful'
        }
    }
}
