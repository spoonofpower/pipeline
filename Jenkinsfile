pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                dir('repos') {
                    parallel(
                        core: {
                            git(
                                url: 'https://github.com/apache/mynewt-core.git',
                                branch: 'master'
                            )
                        },
                        nimble: {
                            git(
                                url: 'https://github.com/apache/mynewt-nimble.git',
                                branch: 'master'
                           )
                        },
                        mcuboot: {
                            git(
                                url: 'https://github.com/runtimeco/mcuboot.git',
                                branch: 'master'
                           )
                        },
                        arduino: {
                            git(
                                url: 'https://github.com/runtimeco/mynewt_arduino_zero.git',
                                branch: 'master'
                           )
                        }
                    )
                }
            }
        }
        stage('Build') {
            steps {
                sh 'echo Build'
                sh 'env'
                sh 'pwd'
                sh 'find .'
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
