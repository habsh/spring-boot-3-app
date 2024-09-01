pipeline {
    agent any
    tools {
        maven "MAVEN"
        jdk "JDK"
    }

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
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin;${PATH}"
                echo "M2_HOME = ${M2_HOME}"
            }
        }
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
