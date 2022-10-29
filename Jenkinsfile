pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: 'select the project version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'do you like to execute tests?')
    }
    stages {
        stage('Build Angular') {
            steps {
                echo 'Starting the Angular build...'
                // sh 'cd C:/ProgramData/Jenkins/.jenkins/workspace/first-pipeline_develop/frontend/app'
                // sh 'npm install'
                // sh 'ng build'
                sh 'ls'
            }
        }
        stage('Test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                echo "Deploying version ${params.VERSION}"
            }
        }
    }
}