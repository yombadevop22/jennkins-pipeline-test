pipeline {
   agent any
   stages{
    stage('codeSCAN'){
        steps{
            sh 'trivy --version'
        
        }
    }
    stage('dockerImageBuild'){
        steps{
            sh 'docker -v'
    }
}
    stage('PushImage'){
        steps{
            sh 'docker ps'
        }
    }
   }
}