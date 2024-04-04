pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/huanmit/spring-petclinic.git'
            }
        }
        
        stage('Build') {
            steps {
                sh './mvnw package'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Local SonarQube') {
                    sh './mvnw sonar:sonar'
                }
            }
        }
        
        stage('Run Application') {
            steps {
                sh 'java -jar target/*.jar'
            }
        }
    }
}
