pipeline {
    agent {
        node {
            label "ubuntu && android"
        }
    }
    environment {
        APPNAME = "TC Smart"
        APPID = "tcsmart"
        PLATFORM = "android"
    }
    options { 
        skipDefaultCheckout() 
    }
    stages {
        stage("Prepare") {
            steps {
                echo "Hello Prepare"
                cleanWs()
                checkout scm
                sh "chmod +x ./prepare.sh && ./prepare.sh"
                echo "Start build: ${env.BUILD_NUMBER}"
                echo "Current build: ${currentBuild.number}"
            }
        }
        
        stage("Build") {
            steps {
                script {
                    for(int i = 0; i < 5; i++) {
                        echo "Script ${i}"
                    }
                    def data = [
                        "name": "Danda",
                        "job": "CEO"
                    ]
                    writeJSON(file: "data_${env.BUILD_NUMBER}.json", json: data)
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