pipeline {
    agent {
        node {
            label "ubuntu && android"
        }
    }
    stages {
        stage("Prepare") {
            steps {
                echo "Hello Prepare"
                sh "chmod +x ./prepare.sh"
                sh "./prepare.sh"
            }
        }
         stage("Install") {
            steps {
                echo("Hello Install")
                sh "./install"
            }
        }
        stage("Build") {
            steps {
                echo("Hello Build")
            }
        }
        stage("Publish") {
            steps {
                echo("Hello Publish")
            }
        }
    }
    post {
        always {
            echo "I always say hello again!"
        }
        success {
            echo "Yay success"
        }
        failure {
            echo "Oh no, failure"
        }
        cleanup {
            echo "Cleanup here.."
        }
    }
}