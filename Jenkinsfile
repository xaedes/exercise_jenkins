pipeline {
    agent {
        dockerfile { 
            label 'linux'
            filename 'Dockerfile' 
        }
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
                    mkdir ws/
                    cd ws/
                    catkin_init_workspace
                    ln -s ../ ./example_ros_pkg
                    cd ..
                    mkdir build/
                    cd build/
                    cmake ../ws/
                    cmake --build .
                    cd -
                    source build/devel/setup.sh
                '''
            }
        }
    }
}
