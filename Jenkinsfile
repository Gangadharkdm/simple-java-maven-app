pipeline {
    agent any
    stages {
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
        stage('Deploy') {
            when {
                expression {
                    return env.BRANCH == 'master'
                }
            }
            steps {
                sh 'docker build -t my-java-app .'
                sh 'docker push my-java-app:latest'
            }
        }
    }
}
