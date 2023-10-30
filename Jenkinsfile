pipeline{
    agent any
    tools{
        jdk 'Java17'
        nodejs 'node16'
    }
    environment {
        SCANNER_HOME=tool 'sonarqube-scanner'
    }
    stages {
        stage('clean workspace'){
            steps{
                cleanWs()
            }
        }
        stage('Checkout from Git'){
            steps{
                git branch: 'main', url: 'https://github.com/ayongpeterking/DevSecOps-Project.git'
            }
        }

        stage("Sonarqube Analysis") {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonarqube4') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        
        }
    }

}    