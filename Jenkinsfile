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
    agent none
    environment {
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
        stage("Stage Android") {
            when {
                expression {
                    return params.Platform == "Android"
                }
            }
            agent {
                node {
                    label "android"
                }
            }
            stages {
                stage("Cleanup") {
                    steps {
                        echo "Cleanup workspace..."
                    }
                }
                stage("Prepare") {
                    steps {
                        echo "Rename name and identifier"
                    }
                }
                stage("Install") {
                    steps {
                        echo "Rename name and identifier"
                    }
                }
                stage("Build") {
                    steps {
                        echo "Rename name and identifier"
                    }
                }
            }
        }
        stage("Stage iOS") {
            when {
                expression {
                    return params.Platform == "iOS"
                }
            }
            agent {
                node {
                    label "ios"
                }
            }
            stages {
                stage("Cleanup") {
                    steps {
                        echo "Cleanup workspace..."
                    }
                }
                stage("Prepare") {
                    steps {
                        echo "Rename name and identifier"
                    }
                }
                stage("Install") {
                    steps {
                        echo "Rename name and identifier"
                    }
                }
                stage("Build") {
                    steps {
                        echo "Rename name and identifier"
                    }
                }
            }
        }
        stage("Publish") {
            echo "Publish app to cloud"
            // input {
            //     message "Can we publish?"
            //     ok "Yes!"
            //     submitter "admin,starlai"
            // }
            // steps {
            //     echo("Hello Publish")
            //     sh 'curl -X GET -u "$CLOUD_USR:$CLOUD_PSW" http://share.twsbp.com/remote.php/dav/files/devop/AppIcon/IC01/res.zip --output ./res.zip'
            //     unzip zipFile: 'res.zip', dir: './android/main'
            // }
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