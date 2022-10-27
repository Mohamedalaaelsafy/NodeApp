pipeline {
    agent none

    stages {
        stage('Build Node App in container') {
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
