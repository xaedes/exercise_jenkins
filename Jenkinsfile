pipeline {
    agent {
        label 'linux'
    }
    stages { 
        stage('Docker') {
            agent {
                dockerfile { filename 'Dockerfile' }
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
                            mkdir build/
                            cd build/
                            cmake ..
                            cmake --build .
                            cd -
                            source build/devel/setup.sh
                        '''
                    }
                }
            }
        }
    }
}
