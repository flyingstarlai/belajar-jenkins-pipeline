pipeline {
    agent {
        node {
            label "ubuntu && android"
        }
    }
    environment {
        PLATFORM = "android"
        CLOUD = credentials("nextcloud")
    }
    parameters {
        string(name: 'APPNAME', defaultValue: 'tcsmart', description: 'Your name...')
        choice(name: 'APPID', chocies:['TCS01', 'TCS02', 'TCS03', 'TCS04', 'TCS05'], description: 'App Identifier\nShould unique' )
    }
    options { 
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
        skipDefaultCheckout()
    }
    stages {
        stage("Prepare") {
            steps {
                echo "Hello Prepare"
                echo "Start build: ${env.BUILD_NUMBER}"
                echo "Current build: ${currentBuild.number}"
                cleanWs()
                checkout scm
                sh "chmod +x ./prepare.sh && ./prepare.sh"
                sh 'echo "Secret: $CLOUD_USR:$CLOUD_PSW" > "rahasia.txt"'
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