pipeline {
    agent any
    triggers{
        githubPush()
    }

    stages{
        stage("Pre"){
            steps {
                checkout scm
            }
        }
        stage("develop"){

            when {
                branch 'develop'
            }
            steps {
                echo "It run only on develop branch"
            }
        }
        stage("feature/test-feature"){
            when {
                branch 'feature/test-feature'
            }
            steps {
                echo "It run only on feature/test-feature branch"
            }
        }

        stage("main"){
            when {
                branch 'main'
            }
            steps {
                echo "It run only on MAIN"

            }
        }
    }
    post {
        success{
            echo "Compled"
        }
        failure{
            echo "NOt"
        }
    }
}
