pipeline {
    agent any
    stages{
        stage('CodeScan'){
            steps{
                sh 'trivy fs . -o result.html'
                
            }
        }
    stage('dockerimagebuild'){
        steps{
            sh 'docker -v'
        }
    }    
    stage('pushimage'){
        steps{
            sh 'docker ps'
        }
    }
    }
}