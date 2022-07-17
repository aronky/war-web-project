pipeline {
    agent any

    stages {
        stage('Git clone') {
            steps {
               git branch: 'master', url: 'https://github.com/aronky/war-web-project.git'
            }
        }
    
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
        
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.89.17.43:8080/')], contextPath: 'path', war: '**/*.war'         }
        }
    }
}
