pipeline {
    agent none
    environment {
        dockerhub = credentials('Docker_Hub')
    }
    stages {
        stage('Build Node App in container') {
            agent { label 'container' }
            steps {
                echo 'Building..'
                sh '''
                // echo $Docker_Hub_PSW | docker login -u $Dcoker_Hub_USR --password-stdin
                docker build -t app .
                docker tag app mohamedalaaelsafy/iti-lab1:v1
                docker push mohamedalaaelsafy/iti-lab1:v1
                '''
            }
        }
        stage('Build Node App in instance') {
            agent { label 'container' }
            steps {
                echo 'Building..'
                sh '''
                // echo $Docker_Hub_PSW | docker login -u $Dcoker_Hub_USR --password-stdin
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
