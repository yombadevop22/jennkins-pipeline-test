pipeline {
   agent any
   stages{
    stage('codeSCAN'){
        steps{
            sh 'trivy fs . -o result.html'
            sh 'cat result.html'
        
        }
    }
    stage('DockerLogin'){
        steps{
            sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 376129840399.dkr.ecr.us-east-1.amazonaws.com'
        }
    }
    stage('dockerImageBuild'){
        steps{
            sh 'docker build -t jenkins-ci .'
            sh ' docker build -t imageversion .'
    }
}
    stage('dockerImageTag'){
        steps{
            sh 'docker tag jenkins-ci:latest 376129840399.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
            sh 'docker tag imageversion 376129840399.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:v1.$BUILD_NUMBER'
        }
    }
    stage('PushImage'){
        steps{
            sh 'docker push 376129840399.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
            sh 'docker push 376129840399.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:V1.$BUILD_NUMBER'
        }
    }
   }
}