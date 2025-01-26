pipeline {
    agent any
    
    tools {
        maven 'maven3'
        jdk 'jdk11'
    }

    stages {
        // stage('Git Checkout') {
        //     steps {
        //         git 'https://github.com/shubham-sihasane/Greetings.git'
        //     }
        // }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
         stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'Tomcat-Deployer', path: '', url: 'http://13.233.100.223:8080')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}
