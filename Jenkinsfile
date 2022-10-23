pipeline {
    agent {
        node {
            label "ubuntu && android"
        }
    }
    stages {
        stage("Hello") {
            steps {
                echo("Hello Pipeline")
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