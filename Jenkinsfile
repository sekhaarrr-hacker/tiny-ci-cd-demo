pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code is already checked out from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                curl -u admin:admin123 \
                -T target/demo.war \
                "http://<TOMCAT_IP>:8080/manager/text/deploy?path=/demo&update=true"
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'curl http://<TOMCAT_IP>:8080/demo/'
            }
        }
    }
}
