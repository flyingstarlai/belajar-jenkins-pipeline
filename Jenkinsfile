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
                sh "./prepare.sh"
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