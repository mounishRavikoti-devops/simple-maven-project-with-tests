pipeline {
    agent any 
    environment {
        JAVA_HOME = "/opt/jdk8"
    }
    stages {
        stage('checkout'){
            steps{
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jglick/simple-maven-project-with-tests.git']]])
        }
        }
        stage('Build') {
            when {
                branch master
            }
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit testResults:'target/surefire-reports/*.xml', skipPublishingChecks: true
                }
            }
        }
       /* stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        } */
    }
}
