pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: 'select the project version')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'do you like to execute tests?')
    }
    stages {
        stage('Build Angular') {
            when {
                expression {
                    env.BRANCH_NAME == 'develop'
                }
            }
            steps {
                echo 'Starting the Angular build...'
                sh 'cd ~/Desktop/estudo/estudoJenkins/frontend/app'
                sh 'npm install'
                sh 'ng build'
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