pipeline {
    agent any
// now we will begin with developing stages according to the task sheet.
    stages {
        // now we will define the first stage for code
        stage('Build') {
            steps {
                echo 'Task: Compile the code using a build tool Apache Maven.'

                echo 'Tool: Apache Maven(used for packaging and compilation)'
            }
        }
        // now we will begin developing second code for second stage
        stage('Unit and Integration Tests') {
            steps {
                echo 'Task: Executing unit tests to validate code functionality and integration tests.'

                echo 'Tools: JUnit and TestNG used for unit testing and integration testing'
            }
            post {

                always {

                    script {


                        def status = currentBuild.currentResult
                        emailext(

                            subject: "Jenkins Pipeline - Unit and Integration Tests Status: ${status}",
                            body: """\
Testing Pipeline after 1st Commit. The Unit and Integration Tests stage has finished with status: ${status}.
Build URL: ${env.BUILD_URL}
""",
                            to: 'gurneetskhehra@gmail.com',

                            attachmentsPattern: '**/test-*.log',

                            replyTo: 'gurneetskhehra@gmail.com'
                        )
                    }
                }
            }
        }
         // now we will begin developing second code for third stage
        stage('Code Analysis') {
            steps {
                echo 'Task: Checking the source code for maintaining quality and adherence to standards.'

                echo 'Tool: SonarQube to ensure code quality and static analysis'
            }
        }
         // now we will begin developing second code for fouth stage
        stage('Security Scan') {
            steps {
                echo 'Task: Scaning the codebase to check for potential security issues.'

                echo 'Tool: OWASP Dependency-Check for catching vulnerability'
            }
            post {
                always {
                    script {
                        def status =  currentBuild.currentResult
                        emailext(
                            subject: "Jenkins Pipeline - Security Scan Status: ${status}",
                            body: """\
Testing Pipeline after 1st Commit. The Security Scan stage has finished with status: ${status}.
Build URL: ${env.BUILD_URL}
""",
                            to: 'gurneetskhehra@gmail.com',
                            attachmentsPattern: '**/dependency-check-*.xml',
                            replyTo: 'gurneetskhehra@gmail.com'
                        )
                    }
                }
            }
        }
         // now we will begin developing second code for fifth stage
        stage('Deploy to Staging') {
            steps {
                echo 'Task: Deploying the application to the staging environment to make preparations for further testing.'

                echo 'AWS CLI to deploy to an AWS EC2 instance'

            }
        }
         // now we will begin developing second code for sixth stage
        stage('Integration Tests on Staging') {
            steps {
                echo 'Task: Performing integration tests in the staging environment.'

                echo 'Tools: Selenium and Postman for UI tests and API testing'
            }
            post {

                always {

                    script {

                        def status = currentBuild.currentResult
                        emailext(
                            subject: "Jenkins Pipeline - Integration Tests on Staging Status: ${status}",
                            body: """\
Testing Pipeline after 1st Commit. The Integration Tests on Staging stage has finished with status: ${status}.
Build URL: ${env.BUILD_URL}
""",
                            to: 'gurneetskhehra@gmail.com',
                            attachmentsPattern: '**/test-*.log',
                            replyTo: 'gurneetskhehra@gmail.com'
                        )
                    }
                }
            }
        }
         // now we will begin developing second code for final stage
        stage('Deploy to Production') {
            steps {
                echo 'Task: Releasing the application to the production environment for live users.'
                
                echo 'AWS CLI to deploy to an AWS EC2 production instance'
            }
        }
    }
}
