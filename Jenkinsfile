def gv

pipeline {
    agent any
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    echo "building jar"
                    //gv.buildJar()
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building image"
                    //gv.buildImage()
                }
            }
        }
        stage("deploy") {
            input {
                message "select the environment to deploy to"
                ok "Done"
                parameters {
                    choice(name: 'one', choices: ['dev', 'staging', 'prod'], descriptions: '')
                    choice(name: 'one', choices: ['dev', 'staging', 'prod'], descriptions: '')                
                }
            }
            steps {
                script {
                    echo "deploying"
                    //gv.deployApp()
                  
                    
                }
            }
        }
    }   
}
