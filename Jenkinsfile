// // pipeline {
// //     agent any
// //     environment {
// //         IMAGE_NAME = "myimage"
// //     }
// //     stages {
// //         stage('Build Docker Image') {
// //             steps {
// //                 script {
// //                     def gitTag = sh(returnStdout: true, script: 'git describe --tags $(git rev-list --tags --max-count=1)').trim()
// //                     def dockerImage = docker.build("${IMAGE_NAME}:${gitTag}", ".")
// //                 }
// //             }
// //         }
// //         stage('Deploy to Kubernetes') {
// //             steps {
// //                 script {
// //                     sh "kubectl apply -f deployment.yaml -n mynamespace --record"
// //                 }
// //             }
// //         }
// //     }
// // }
// pipeline {
//     agent {
//         docker {
//             image 'maven:3-alpine'
//         }
//     }
//     stages {
//         stage('Checkout Code') {
//             steps {
//                 checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-creds', url: 'https://github.com/<username>/<repo>.git']]])
//             }
//         }
//         stage('Build Docker Image') {
//             steps {
//                 sh 'docker build -t custom-nginx -f Dockerfile .'
//             }
//         }
//         // stage('Push to Docker Hub') {
//         //     steps {
//         //         withDockerRegistry([credentialsId: 'dockerhub-creds', url: 'https://index.docker.io/v1/']) {
//         //             sh 'docker push custom-nginx'
//         //         }
//         //     }
//         // }
//         // stage('Deploy to Kubernetes') {
//         //     steps {
//         //         withKubeConfig([credentialsId: 'k8s-cluster-creds']) {
//         //             sh 'kubectl apply -f deployment.yml'
//         //         }
//         //     }
//         // }
//     }
// }
// pipeline {
//     agent any
//     stages {
//         stage('Checkout Code') {
//             steps {
//                 checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitlogin', url: 'https://github.com/jozsoka2222/jenkins-tan-projekt.git']]])
//             }
//         }
//         stage('Build Docker Image') {
//             steps {
//                 sh 'docker build -t custome-nginx -f Dockerfile .'
//             }
//         }
//         // stage('Push to Docker Hub') {
//         //     steps {
//         //         withDockerRegistry([credentialsId: 'dockerhub-creds', url: 'https://index.docker.io/v1/']) {
//         //             sh 'docker push custom-nginx'
//         //         }
//         //     }
//         // }
//         // stage('Deploy to Kubernetes') {
//         //     steps {
//         //         withKubeConfig([credentialsId: 'k8s-cluster-creds']) {
//         //             sh 'kubectl apply -f deployment.yml'
//         //         }
//         //     }
//         // }
//     }
// }
pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
        }
    }
    stages {
        // stage('Checkout Code') {
        //     steps {
        //         checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitlogin', url: 'https://github.com/jozsoka2222/jenkins-tan-projekt.git']]])
        //     }
        // }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-conatiner -f Dockerfile .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push jenkins-conatiner'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig([credentialsId: 'k8s-cluster-creds']) {
                    sh 'helm install mychart ./mychart'
                }
            }
        }
    }
}
