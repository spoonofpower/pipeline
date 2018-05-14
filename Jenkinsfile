pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                parallel(
                    core: {
                        dir('repos/mynewt-core') {
                            git(
                                url: 'https://github.com/apache/mynewt-core.git',
                                branch: 'master'
                            )
                        }
                    },
                    nimble: {
                        dir('repos/mynewt-nimble') {
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
                    arduino: {
                        dir('repos/mynewt_arduino_zero') {
                            git(
                                url: 'https://github.com/runtimeco/mynewt_arduino_zero.git',
                                branch: 'master'
                            )
                        }
                    }
                )
            }
        }
        stage('Build') {
            steps {
                sh 'cd repos/mynewt-core && git status && ls'
                sh 'cd repos/mynewt-nimble && git status && ls'
                sh 'cd repos/mcuboot && git status && ls'
                sh 'cd repos/mynewt_arduino_zero && git status && ls'
                sh 'env'
                sh 'pwd'
                sh 'echo "From Build Step" > info.txt'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Test'
                sh 'cat info.txt'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploy'
                sh 'cat info.txt'
            }
        }
    }
}
