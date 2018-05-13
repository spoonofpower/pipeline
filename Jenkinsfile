pipeline {
    agent any
    stages {
        stage('Checkout') {
            dir('repos') {
                git(
                    url: 'https://github.com/apache/mynewt-core.git',
                    branch: 'master'
                )
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
