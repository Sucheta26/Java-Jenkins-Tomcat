pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout Code') {
    steps {
        git branch: 'main',
            url: 'https://github.com/Sucheta26/Java-Jenkins-Tomcat.git'
    }
}

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-cred',
                        path: '',
                        url: 'http://13.206.144.126:8080'
                    )
                ],
                contextPath: '',
                war: 'ROOT.war'
            }
        }
    }
}
