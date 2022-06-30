pipeline {
    agent {
        docker { image 'ros:melodic-ros-base-bionic' }
    }
    stages {
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                    git status
                    git clean -x -f -d
                    git status
                    find .
                    source /opt/ros/melodic/setup.sh
                    export | grep PATH
                    catkin_init_workspace
                    echo cmake -B build/ -S .
                    cmake -B build/ -S .
                    echo cmake --build build/
                    cmake --build build/
                    source build/devel/setup.sh
                '''
                
            }
        }
    }
}
