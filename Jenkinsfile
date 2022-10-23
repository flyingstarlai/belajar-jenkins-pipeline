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
        
        stage("Build") {
            steps {
                script {
                    for(int i = 0; i < 10; i++) {
                        echo "Script ${i}"
                    }
                }
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