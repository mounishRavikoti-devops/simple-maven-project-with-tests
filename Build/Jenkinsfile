pipeline {
    agent any
    environment{
        JAVA_HOME = "/opt/java8/"
    }
    
    tools {
      maven 'maven2'
    }

   
       stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests=true clean package'
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
