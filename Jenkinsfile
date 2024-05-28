pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "Building the code using Maven"
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                echo "Running unit tests with JUnit"
                echo "Running integration tests with Selenium"
            }
        }

        stage("Code Analysis") {
            steps {
                echo "Running code analysis with SonarQube"
            }
        }

        stage("Security Scan") {
            steps {
                echo "Running security scan with OWASP ZAP"
            }
            post {
                success {
                    emailext(
                        to: "mariaelsasimon2002@gmail.com",
                        subject: "Build status email",
                        body: "Build was successful",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "mariaelsasimon2002@gmail.com",
                        subject: "Build status email",
                        body: "Build was failed",
                        attachLog: true
                    )
                }
            }
        }

        stage("Deploy to Staging") {
            steps {
                echo "Deploying the application to staging server using AWS CodeDeploy"
            }
            post {
                success {
                    emailext(
                        to: "mariaelsasimon2002@gmail.com",
                        subject: "Build status email",
                        body: "Build was successful",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "mariaelsasimon2002@gmail.com",
                        subject: "Build status email",
                        body: "Build was failed",
                        attachLog: true
                    )
                }
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo "Running integration tests on the staging environment with Selenium"
            }
            post {
                success {
                    emailext(
                        to: "mariaelsasimon2002@gmail.com",
                        subject: "Build status email",
                        body: "Build was successful",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "mariaelsasimon2002@gmail.com",
                        subject: "Build status email",
                        body: "Build was failed",
                        attachLog: true
                    )
                }
            }
        }

        stage("Deploy to Production") {
            steps {
                echo "Deploying the application to production server using AWS CodeDeploy"
            }
        }
    }

    post {
        always {
            script {
                echo 'Pipeline finished. Sending notification emails...'
            }
        }
        success {
            emailext(
                to: env.RECIPIENTS,
                subject: "Jenkins Pipeline: ${currentBuild.fullDisplayName} - SUCCESS",
                body: """<p>Build status: ${currentBuild.currentResult}</p>
                         <p>Check the console output at ${env.BUILD_URL} to view the results.</p>""",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: env.RECIPIENTS,
                subject: "Jenkins Pipeline: ${currentBuild.fullDisplayName} - FAILURE",
                body: """<p>Build status: ${currentBuild.currentResult}</p>
                         <p>Check the console output at ${env.BUILD_URL} to view the results.</p>""",
                attachLog: true
            )
        }
    }
}