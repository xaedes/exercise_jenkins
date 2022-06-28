pipeline {
    // https://www.jenkins.io/blog/2019/11/22/welcome-to-the-matrix/
    parameters {
        choice(name: 'PLATFORM_FILTER', choices: ['all', 'linux', 'win'], description: 'Run on specific platform')
    }
    agent none
    stages {
        stage('BuildTestDeploy') {
            matrix {
                when {
                    anyOf {
                        expression { params.PLATFORM_FILTER == 'all' }
                        expression { params.PLATFORM_FILTER == env.PLATFORM }
                    }
                }
                axes {
                    axis {
                        name 'PLATFORM'
                        values 'linux', 'win'
                    }
                }
                stages {
                    stage('Linux') {
                        when {
                            expression { env.PLATFORM == 'linux' }
                        }
                        matrix {
                            agent {
                                label "${PLATFORM}-${TOOLCHAIN}-node"
                            }                            
                            axes {
                                axis {
                                    name 'TOOLCHAIN'
                                    values 'ubuntu-focal'
                                }
                            }
                            stages {
                                stage('${PLATFORM}-Build') {
                                    steps {
                                        echo 'Linux-Build ${PLATFORM}-${TOOLCHAIN}' 
                                    }
                                }
                                stage('${PLATFORM}-Test') {
                                    steps {
                                        echo 'Linux-Test ${PLATFORM}-${TOOLCHAIN}' 
                                    }
                                }
                                stage('${PLATFORM}-Deploy') {
                                    steps {
                                        echo 'Linux-Deploy ${PLATFORM}-${TOOLCHAIN}' 
                                    }
                                }
                            }
                        }
                    }
                    stage('Win') {
                        when {
                            expression { env.PLATFORM == 'win' }
                        }
                        matrix {
                            agent {
                                label "${PLATFORM}-${TOOLCHAIN}-node"
                            }                            
                            axes {
                                axis {
                                    name 'TOOLCHAIN'
                                    values 'ubuntu-focal'
                                }
                            }
                            stages {
                                stage('${PLATFORM}-Build') {
                                    steps {
                                        echo 'Win-Build ${PLATFORM}-${TOOLCHAIN}' 
                                    }
                                }
                                stage('${PLATFORM}-Test') {
                                    steps {
                                        echo 'Win-Test ${PLATFORM}-${TOOLCHAIN}' 
                                    }
                                }
                                stage('${PLATFORM}-Deploy') {
                                    steps {
                                        echo 'Win-Deploy ${PLATFORM}-${TOOLCHAIN}' 
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
