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
                bat 'cd frontend\\app && npm install'
                bat 'cd frontend\\app && ng lint'
                bat 'cd frontend\\app && npm run test --watch=false'
                bat 'cd frontend\\app && ng build'
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