pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Kirtinaidu-20/JenkinsProject.git'
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
        stage('Deploy') {
            steps {
                sh 'cp target/vivekapp.war /var/lib/tomcat9/webapps/'
                sh 'sudo systemctl restart tomcat9'
            }
        }
    }
}
