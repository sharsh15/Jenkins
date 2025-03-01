pipeline {
    agent any

    stages {
        stage('cloning the github repo') {
            steps {
                bat "cmd /c rmdir /s /q Pipeline"
                bat "cmd /c git clone https://github.com/sharsh15/Pipeline.git"   
            }
        }
        stage('building the jar file') {
            steps {
                dir('Pipeline'){
                    bat "cmd /c cd"
                    bat "cmd /c mvn clean install"
                }
            }
        }
        stage('running the jar file') {
            steps {
                dir('Pipeline/target') {
                bat "java -jar mavenproject-0.0.1-SNAPSHOT.jar"
                }
            }
        }
    }
}
