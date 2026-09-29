pipeline {
    agent any

    environment{
        deploydir="/var/lib/tomcat11/webapps"
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
                sh 'sudo cp -rvf target/task-manager.war ${deploydir}'
                sh 'sudo systemctl restart tomcat'
            }
        }
       
    }

    post{
        success{
            echo"Successfull!1"
        }

        failure{
            echo"failed"
        }
    }
}
