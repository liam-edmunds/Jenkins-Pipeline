pipeline{
    agent any
    environment{
        DIRECTORY_PATH = "/Users/liamedmunds/Desktop/Semester 2 2024/Professional Practices"
        TESTING_ENVIRONMENT = "SIT223 Testing Environment"
        PRODUCTION_ENVIRONMENT = "Liam Edmunds"
    }
    stages{
        stage('Build'){
            steps{
                echo "Fetch the source code from the directory path specified by the environment variable"
            }
            post{
                always{
                    mail to: "liamtedmunds@gmail.com",
                    subject: "Build Status Email",
                    body: "Build log attached!"
        }
        stage('Test'){
            steps{
                echo "Unit tests"
                echo "Integration tests"
            }
        }
        stage('Code Quality Check'){
            steps{
                echo "Check the quality of the code"
            }
        }
        stage('Deploy'){
            steps{
                echo "Deploy the application to a testing environment specified by the environment variable"
                    
            }
        }
        stage('Approval'){
            steps{
                sleep 10
            }
        }
        stage('Deploy to Production'){
            steps{
                echo "Code is deployed to production environment: $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}
