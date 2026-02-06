pipeline{
    agent any
    stages{
        stage("Install dependencies"){
            steps{
                bat 'npm install'
            }
        }
        stage("Fix vulnerabilities"){
            steps{
                bat 'npm audit fix'
            }
        }
        parallel{
        failFast true
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
}