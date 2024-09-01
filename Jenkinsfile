pipeline {
    agent any
    stages {
       stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master',
                        credentialsId: 'Credential ID',
                        url: 'https://github.com/habsh/microservice1.git'
                }
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
