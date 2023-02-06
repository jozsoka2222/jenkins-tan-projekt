// CODE_CHANGES = getGitChanges()
pipeline {
    agent any
    // environment {
    //     NEW_VERSION = '1.3.0'
    // }
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
            // when{
            //     expression{
            //         BRANCH_NAME == 'main' && CODE_CHANGES == true
            //     }
            // }
            steps {
                echo 'building the application...'
            }
        }
        stage('test'){
            // when{
            //     expression{
            //         BRANCH_NAME == 'main'
            //     }
            // }
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
    // post{
    //     always {

    //     }
    //     success{

    //     }
    //     failure{

    //     }
    // }
}
