pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Building code using Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests"
                echo "Executing Selenium testing tool"
            }
            post {
                always {
                    script {
                        def logFile = "${env.WORKSPACE}/test-stage-log.txt"
                        sh "echo '${currentBuild.rawBuild.getLog(1000).join("\n")}' > ${logFile}"
                        def status = currentBuild.currentResult
                        emailext attachLog: false,
                                 attachmentsPattern: 'test-stage-log.txt',
                                 to: 'liamtedmunds@gmail.com',
                                 subject: "Test Stage Status: ${status}",
                                 body: "The Unit and Integration Tests stage has finished with status: ${status}. Check the attached logs for more details."
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Check the quality of the code"
                echo "Executing SonarQube analysis tool"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Perform security scan"
                echo "Executing OWASP CodeSonar"
            }
            post {
                always {
                    script {
                        def logFile = "${env.WORKSPACE}/security-scan-log.txt"
                        sh "echo '${currentBuild.rawBuild.getLog(1000).join("\n")}' > ${logFile}"
                        def status = currentBuild.currentResult
                        emailext attachLog: false,
                                 attachmentsPattern: 'security-scan-log.txt',
                                 to: 'liamtedmunds@gmail.com',
                                 subject: "Security Scan Status: ${status}",
                                 body: "The Security Scan stage has finished with status: ${status}. Check the attached logs for more details."
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying application to AWS EC2 server"
            }
        }
        stage('Integration tests on staging') {
            steps {
                echo "Running integration tests to ensure application functions as expected"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy application to production server, AWS EC2"
            }
        }
    }
}
