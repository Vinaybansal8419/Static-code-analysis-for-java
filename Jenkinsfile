pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/OT-MICROSERVICES/salary-api.git'
            }
        }
        stage('analyze') {
            steps {
                script {
                    // Navigate to the root directory where the pom.xml file is located
                    dir('/var/lib/jenkins/workspace/code-compilation') {
                        // List files for debugging
                        sh 'ls -R'
                    }
                    // Assuming the pom.xml is at the root of the repository
                    sh 'mvn checkstyle:check' // Build the project and install dependencies
                    
                    }
            }
        }
    }
    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
