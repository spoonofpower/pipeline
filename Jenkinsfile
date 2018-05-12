pipeline {
    agent any
    stages {
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
