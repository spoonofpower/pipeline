pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                parallel(
                    core: {
                        dir('repos') {
                            git(
                                url: 'https://github.com/apache/mynewt-core.git',
                                branch: 'master'
                            )
                        }
                    },
                    nimble: {
                        dir('repos') {
                            git(
                                url: 'https://github.com/apache/mynewt-nimble.git',
                                branch: 'master'
                            )
                        }
                    },
                    mcuboot: {
                        dir('repos') {
                            git(
                                url: 'https://github.com/runtimeco/mcuboot.git',
                                branch: 'master'
                            )
                        }
                    },
                    arduino: {
                        dir('repos') {
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
                sh 'echo Build'
                sh 'env'
                sh 'pwd'
                sh 'ls repos'
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
