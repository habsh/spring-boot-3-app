pipeline {
    agent any
    stages {
       stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master',
                        credentialsId: 'habgithub',
                        url: 'https://github.com/habsh/spring-boot-3-app.git'
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
