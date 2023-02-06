
pipeline {
    agent any

    tools{
        kubernetes
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('build') {

            steps {
                echo 'building the application...'
            }
        }
        stage('test'){

            steps {
                echo 'testing the application...'
            }
        }
        stage('deploy'){
            steps {
                echo 'deploying the application...'
            }
        }
    }
}
