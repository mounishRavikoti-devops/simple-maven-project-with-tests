pipeline {
    agent any
    environment{
        JAVA_HOME = "/opt/java8/"
    }
   
       stages {
        stage('Build') {
            steps {
                sh '/opt/maven3.8.4/bin/mvn -B -DskipTests=true clean package'
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
        /*stage('Deliver') {
            steps {
               sh './jenkins/scripts/deliver.sh'
            }
        }  */
    }
}
