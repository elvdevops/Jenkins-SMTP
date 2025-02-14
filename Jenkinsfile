pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add your build commands here, e.g.,
                // sh 'mvn clean package' or sh './build.sh'
            }
        }
    }

    post { 
        success {
            emailext subject: "Jenkins Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                     body: "Good news! The build was successful.\nCheck details at: ${env.BUILD_URL}",
                     to: 'elvdevops@gmail.com'
        }
        failure {
            emailext subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                     body: "Oops! The build failed.\nCheck details at: ${env.BUILD_URL}",
                     to: 'elvdevops@gmail.com'
        }
    }
}
