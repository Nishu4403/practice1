pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/Nishu4403/practice1.git'
        NGINX_PATH = 'C:\\Users\\nisha\\OneDrive\\Desktop\\jenk\\nginx-1.24.0\\htmldocs'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Use the checkout step to clone the Git repository
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[git credentialsId: 'git1', url: 'https://github.com/Nishu4403/practice1.git']]])
                }
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // Using the Jenkins workspace variable to reference files
                    bat 'xcopy /y "C:\\Users\\nisha\\OneDrive\\Desktop\\dvps practice 1\\index.html" "%NGINX_PATH%"'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! You can add additional steps here.'
        }
        failure {
            echo 'Pipeline failed! You may want to take some actions.'
        }
    }
}
