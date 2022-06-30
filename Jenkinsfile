pipeline {
    agent {
        docker { image 'ros:melodic-ros-base-bionic' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'cmake --version'
            }
        }
    }
}
