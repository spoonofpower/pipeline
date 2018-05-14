pipeline {
    agent any

    environment {
        GOPATH = "$WORKSPACE/go"
        PATH = "$PATH:$GOPATH/bin"
    }

    stages {
        stage('Checkout') {
            steps {
                parallel(
                    core: {
                        dir('repos/apache-mynewt-core') {
                            git(
                                url: 'https://github.com/apache/mynewt-core.git',
                                branch: 'master'
                            )
                        }
                    },
                    nimble: {
                        dir('repos/apache-mynewt-nimble') {
                            git(
                                url: 'https://github.com/apache/mynewt-nimble.git',
                                branch: 'master'
                            )
                        }
                    },
                    mcuboot: {
                        dir('repos/mcuboot') {
                            git(
                                url: 'https://github.com/runtimeco/mcuboot.git',
                                branch: 'master'
                            )
                        }
                    },
                    mynewt_runtime: {
                        dir('repos/mynewt_runtime') {
                            git(
                                url: 'https://github.com/runtimeinc/mynewt_runtime.git',
                                branch: 'master',
                                credentialsId: 'github',
                            )
                        }
                    },
                    arduino: {
                        dir('repos/mynewt_arduino_zero') {
                            git(
                                url: 'https://github.com/runtimeco/mynewt_arduino_zero.git',
                                branch: 'master'
                            )
                        }
                    },
                    runtime: {
                        dir("$GOPATH/src/github.com/runtimeinc/runtime") {
                            git(
                                url: 'https://github.com/runtimeinc/runtime.git',
                                branch: 'master',
                                credentialsId: 'github',
                            )
                        }
                    }
                )
            }
        }
        stage('Install Tools') {
            steps {
                sh 'go install github.com/runtimeinc/runtime'
                sh 'go get mynewt.apache.org/newt/newt'
                sh 'go get mynewt.apache.org/newtmgr/newtmgr'
            }
        }
        stage('Run Jobs') {
            steps {
                sh 'newt build testbench-coap-nrf52'
            }
        }
    }
}
