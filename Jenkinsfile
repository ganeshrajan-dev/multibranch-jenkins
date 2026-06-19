 pipeline {
        agent any

        triggers {
            githubPush()
        }

        stages {
            stage('Checkout') {
                steps {
                    checkout scm
                }
            }

            stage('Build') {
                steps {
                    echo "Building branch: ${env.BRANCH_NAME}"
                    sh 'echo "Compiling application..."'
                }
            }

            stage('Unit Test') {
                steps {
                    sh 'echo "Running unit tests..."'
                    sh 'echo "Tests passed!"'
                }
            }

            stage('Deploy to Dev') {
                when {
                    branch 'develop'
                }
                steps {
                    echo 'Deploying to DEV environment...'
                    sh 'echo "Dev deployment done!"'
                }
                steps {
                    echo "In the Dev env adding steps"
                    sh 'ls'
                }
            }

            stage('Deploy to Production') {
                when {
                    branch 'main'
                }
                steps {
                    echo 'Deploying to PRODUCTION...'
                    sh 'echo "Production deployment done!"'
                }
            }

            stage('PR Validation') {
                when {
                    changeRequest()
                }
                steps {
                    echo "Validating PR #${env.CHANGE_ID}"
                    sh 'echo "Code quality check..."'
                    sh 'echo "Integration tests..."'
                }
            }
        }

        post {
            success {
                echo "Pipeline SUCCESS for branch: ${env.BRANCH_NAME}"
            }
            failure {
                echo "Pipeline FAILED for branch: ${env.BRANCH_NAME}"
            }
            always {
                cleanWs()
            }
        }
    }
