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
                sh """
                curl -u admin:admin123 \
                -T target/tiny-ci-cd-demo-1.0.war \
                "http://3.110.106.39:8080/manager/text/deploy?path=/demo&update=true"
                """
            }
        }

        stage('Verify') {
            steps {
                sh 'curl -f http://3.110.106.39:8080/demo/'
            }
        }
    }
}
