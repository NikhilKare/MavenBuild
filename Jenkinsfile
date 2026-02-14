pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/hkshitesh/MavenBuild.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                  tomcat9(
                    credentialsId: 'tomcat-id',
                    url: 'http://localhost:9090'
                  )
                ],
                contextPath: '/simpleapp',
                war: 'target/*.war'
            }
        }
    }
}
