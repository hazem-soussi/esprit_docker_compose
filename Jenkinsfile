pipeline {
    agent any

    stages {
        stage('Testing Environment') {
            steps {
                dir("tpAchatProject/") {
                    sh 'mvn test -Dtest=ControllerAndServiceSuite'
                    sh 'mvn test -Dtest=IntegrationSuite'
                    sh 'mvn test -DfailIfNoTests=false'
                }
            }
        }
        stage('Build') {
            steps {
                dir("tpAchatProject/"){
                    sh 'mvn install -DskipTests'
                }
            }
        }
        stage('Docker compose') {
            steps {
                sh 'sudo docker-compose build'
                sh 'sudo docker-compose up -d'
            }
        }
        stage('end2end Tests') {
            steps {
                dir("tpAchatProject/") {
                    sh 'mvn test -Dtest=SeleniumSuite'
                }
            }
        }
    }
}
