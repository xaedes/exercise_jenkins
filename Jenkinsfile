pipeline {
    agent {
        docker { image 'ros:melodic-ros-base-bionic' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'source /opt/ros/melodic/setup.sh'
                sh 'export | grep PATH'
            }
        }
    }
}
