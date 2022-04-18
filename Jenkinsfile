#!/usr/bin/env groovy

node {
    stage('Stage 1') {
        echo 'hello'
    }
    stage(codecheckout){
    checkout([$class: 'GitSCM', 
              branches: [[name: '*/master']],
              extensions: [],
              userRemoteConfigs: [[url: 'https://github.com/mounishRavikoti-devops/simple-maven-project-with-tests.git']]])
}
}
