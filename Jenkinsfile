pipeline {
    agent any

    tools {
    maven 'Maven-3.9.12'
    jdk 'jdk25.0.2'
}


    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/VedTeredesai7137/DevOps-Exp-4.git'
                 
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        path: '',
                        url: 'http://localhost:8081'
                    )
                ],
                contextPath: 'hello-world-webapp',
                war: 'target/hello-world-webapp.war'
            }
        }
    }
}
