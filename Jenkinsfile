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
                echo "Cloning this ${params.GithubURL} in ${params.Environment}"             
                sh "git clone${params.Github-url}"   
            }
        }
        stage('building the jar file') {
            steps {
                    dir('Pipeline'){
                    sh "pwd"
                    sh "mvn clean install"
                }
            }
        }
        stage('running the jar file') {
            steps {
                dir('Pipeline/target') {
                sh "java -jar mavenproject-0.0.1-SNAPSHOT.jar"
                }
            }
        }
    }
}
