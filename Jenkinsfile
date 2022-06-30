pipeline {
    agent {
        docker { image 'ros:melodic-ros-base-bionic' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'sh source /opt/ros/melodic/setup.sh && export | grep PATH'
                
            }
        }
    }
}
