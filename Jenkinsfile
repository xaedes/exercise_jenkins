pipeline {
    agent {
        docker { image 'ros:melodic-ros-base-bionic' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                    find .
                    source /opt/ros/melodic/setup.sh
                    export | grep PATH
                    catkin_init_workspace
                    cmake -B build/ -S .
                    cmake --build build/
                    source build/devel/setup.sh
                '''
                
            }
        }
    }
}
