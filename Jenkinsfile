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
                bat 'npm audit fix --force'
            }
        }
        failFast true
        stage("Check and test"){
            parallel{
                //failFast true
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
}