pipeline {
   agent any
   stages{
    stage('clone'){
        steps{
            sh 'echo "clone"'
            sh 'uname -r'
            sh 'cat /etc/os-release'
        }
    }
    stage('test'){
        steps{
            sh 'echo "test"'
    }
}
    stage('createfile'){
        steps{
            sh 'touch text-$BUILD-ID'
        }
    }
   }
}