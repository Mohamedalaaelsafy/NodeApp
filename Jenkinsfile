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
               sh "docker login -u $dockerhub_USR -p $dockerhub_PSW"
               sh 'docker build -t app .'
               sh 'docker tag app mohamedalaaelsafy/iti-lab1:v1'
               sh 'docker push mohamedalaaelsafy/iti-lab1:v1'
                
            }
        }
        stage('Build Node App in instance') {
            agent { label 'instance' }
            steps {
               sh 'echo Building..'
               sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
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
