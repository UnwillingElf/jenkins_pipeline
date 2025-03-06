pipeline {
    agent any
    stages{
        stage('CodeScan'){
            steps{
                sh 'trivy fs . -o result.html'
                sh 'cat result.html'
                
            }
        }
        stage('dockerlogin'){
            steps{                                         
                sh'aws ecr get-login-password --region us-east-1 | \
                docker login --username AWS --password-stdin \
                605134461718.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
    stage('dockerimagebuild'){
        steps{
            sh 'docker build -t  jenkins-ci .'
        }
    }    
    stage ('dockerimagetag'){
        steps{
            sh 'docker tag jenkins-ci:latest 605134461718.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
        }
    }
    stage('pushimage'){
        steps{
            sh 'docker push 605134461718.dkr.ecr.us-east-1.amazonaws.com/jenkins-ci:latest'
        }
    }
    }
}