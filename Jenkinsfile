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
                cleanWs()
                sh "chmod +x ./prepare.sh && ./prepare.sh tcsmart"
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
                    writeJSON(file: "data_test.json", json: data)
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