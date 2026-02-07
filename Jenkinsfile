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
                bat 'npm audit fix --force || exit 0'
            }
        }
        stage("Fix vulnerabilities 2"){
            steps{
                bat 'npm audit fix --force --audit-level=high'
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
        stage("Approval to Deploy"){
            steps{
                input message: 'Do you want to deploy to production?', ok: 'Deploy'
            }
        }
        stage("Deploy to production"){
            steps{
                echo "Deploying to production..."
            }
        }
    }
}