#!/usr/bin/env groovy

def gv

pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage("init") {
            steps {
                script {
                   gv = load "script.groovy"
                }
            }
        }
        stage("build") {
            steps {
                script {
                    gv.buildJar()
                }
            }
        }
        stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }
        }
        stage("deploy") {
            input {
                message "select the environment to deploy to if it triggered"
                ok "Done"
                parameters {
                    choice(name: 'one', choices: ['dev', 'staging', 'prod'], description: '')                
                }
            }
             steps {
                script {
                    env.ENV = input message: "Select the environment to deploy to", ok: "Done", parameters: [choice(name: 'ONE', choices: ['dev', 'staging', 'prod'], description: '')]

                    gv.deployApp()
                    echo "Deploying to ${ENV} true"
                }
            }
        }
    }
}


       
