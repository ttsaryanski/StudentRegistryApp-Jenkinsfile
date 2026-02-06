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
        stage("Fix vulnerabilities 2"){
            steps{
                bat 'npm audit fix'
            }
        }
        stage("Check and test"){
            parallel{
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