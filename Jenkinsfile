properties([
    parameters([
        [
            $class: 'ChoiceParameter',
            choiceType: 'PT_SINGLE_SELECT',
            name: 'Platform',
            script: [
                $class: 'ScriptlerScript',
                scriptlerScriptId:'getPlatforms.groovy'
            ]
        ],
         [
            $class: 'CascadeChoiceParameter',
            choiceType: 'PT_SINGLE_SELECT',
            name: 'Icon',
            referencedParameters: 'Platform',
            script: [
                $class: 'ScriptlerScript',
                scriptlerScriptId:'getPlatformIcons.groovy',
                parameters: [
                    [name:'Platform', value: '$Platform']
                ]
            ]
        
        ]
    ])
])

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
    // triggers {
    //     cron("*/5 * * * *")
    // }
    parameters {
        string(name: 'APPNAME', defaultValue: 'TC Smart', description: 'Your name...')
    }
    options { 
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
        skipDefaultCheckout()
    }
    stages {
        stage("Prepare:iOS") {
            when {
                equals(actual: params.Platform, expected: "ios")
            }
            steps {
                echo "Preparing for iOS"
                // nodejs(nodeJSInstallationName: 'Node 18') {
                //     echo "Hello Prepare"
                //     echo "Start build: ${env.BUILD_NUMBER}"
                //     echo "Current build: ${currentBuild.number}"
                //     cleanWs()
                //     checkout scm
                //     sh "chmod +x ./prepare.sh && ./prepare.sh"
                //     sh 'echo "Secret: $CLOUD_USR:$CLOUD_PSW" > "rahasia.txt"'
                // }    
            }
        }
           stage("Prepare:android") {
            when {
                equals(actual: params.Platform, expected: "android")
            }
            steps {
                echo "Preparing for android"
            }
        }
        stage("Build") {
            steps {
                script {
                    // for(int i = 0; i < 5; i++) {
                    //     echo "Script ${i}"
                    // }
                    def data = [
                        "name": "Danda",
                        "job": "CEO"
                    ]
                    writeJSON(file: "data_${env.BUILD_NUMBER}.json", json: data)
                }
            }
        }
        stage("Publish") {
            // input {
            //     message "Can we publish?"
            //     ok "Yes!"
            //     submitter "admin,starlai"
            // }
            steps {
                echo("Hello Publish")
                sh 'curl -X GET -u "$CLOUD_USR:$CLOUD_PSW" http://share.twsbp.com/remote.php/dav/files/devop/AppIcon/IC01/res.zip --output ./res.zip'
                unzip zipFile: 'res.zip', dir: './android/main'
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