pipeline {
    agent any

    environment {
        deploydir = "/var/lib/tomcat11/webapps"
    }

    stages {
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
                // Copy the WAR file built by Maven
                sh 'sudo cp -rvf target/vivekapp.war ${deploydir}/vivekapp.war'
                // Restart the correct Tomcat service
                sh 'sudo systemctl restart tomcat11'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful! Application is live on Tomcat11.'
        }
        failure {
            echo 'Deployment failed. Please check logs.'
        }
    }
}
