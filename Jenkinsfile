pipeline {
    agent any

    tools {
        maven 'Maven'     // Name configured in Jenkins
        jdk 'JDK'         // Name configured in Jenkins
    }

    environment {
        DEPLOY_DIR = '/opt/tomcat/webapps'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/parsh1002/Devopstest_Program3.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                echo "Deploying WAR file..."
                cp target/Program3.war
                '''
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}
