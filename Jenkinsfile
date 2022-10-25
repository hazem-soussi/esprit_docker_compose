pipeline {
    agent any

    stages {
     // main SATGES
        stage ("1st stage : Git checkout PLEAASE"){
            steps{
        git branch: 'main', 
            url: 'https://github.com/hazem-soussi/projet_esprit.git'
            }
        
        }
    
        
                stage('2nd Stage : Maven Build Project') {
            steps {
                echo "Build our project"
                sh 'mvn clean install '
            }
        }
        
        
        

        
             stage ("3rd Stage : unit testing"){
            steps{
                sh "mvn test"
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
