pipeline {
    agent any

    environment {
        RECIPIENTS = 'elvdevops@gmail.com' // Change this to your email recipients
    }

    stages {
        stage('Build') { 
            steps { 
                script {
                    echo 'Building...'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running Tests...'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying...'
                }
            }
        }
    }

    post {
        always {
            script {
                def status = currentBuild.result ?: 'SUCCESS'
                emailext subject: "${status}: Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                         body: "The build status is ${status}.\nCheck console output at ${env.BUILD_URL}.",
                         to: "${RECIPIENTS}"
            }
        }
    }
}
