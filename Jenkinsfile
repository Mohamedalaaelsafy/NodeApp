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
            //    sh 'echo $DOCKER_Hub_PWD | docker login -u $Dcoker_Hub_USER --password-stdin'
               sh 'docker build -t app .'
               sh 'docker tag app mohamedalaaelsafy/iti-lab1:v1'
               sh 'docker push mohamedalaaelsafy/iti-lab1:v1'
                
            }
        }
        stage('Build Node App in instance') {
            agent { label 'container' }
            steps {
                echo 'Building..'
                sh '''
                docker login --username Docker_Hub_USR --password Docker_Hub_PSW
                docker build -t app .
                docker tag app mohamedalaaelsafy/iti-lab1:v1
                docker push mohamedalaaelsafy/iti-lab1:v1
                '''
            }
        }
    }

    post {
        success {
            echo 'This will run only if successful'
        }
    }
}
