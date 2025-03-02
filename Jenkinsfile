pipeline {
    agent any

    parameters{
        string(name: 'GithubURL', defaultValue: 'URL', description: 'Please enter the Gitbut repository url for repo cloning')
        choice(name: 'Environment', choices: ['Development', 'Testing', 'Production'], description: 'Pick environment to clone the git repo')
    }

    stages {
        stage('cloning the github repo') {
            steps {
                deleteDir()
               // bat "cmd /c rmdir /s /q Pipeline"
                echo "Cloning this ${params.GithubURL} in ${params.Environment}"             
                bat "cmd /c git clone ${params.GithubURL}"   
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
