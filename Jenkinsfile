pipeline{
    agent any
    stages{
        stage("Install dependencies"){
            steps{
                bat 'npm install'
            }
        }
        stage("Run security checks"){
            steps{
                bat 'npm audit'
            }
        }
        stage("Run tests"){
            steps{
                bat 'npm test'
            }
        }
    }
}