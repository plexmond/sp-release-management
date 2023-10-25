pipeline {
    agent any

    stages {
        stage('Build and Test') {
            steps {
                // build phase
                echo "build"
            }
        }

        stage('Dev Approval') {
            when {
                branch 'dev' // only when dev branch
            }
            steps {
                input 'Approve the changes to push to main?' // approve manually
            }
        }

        stage('Push to Main') {
            when {
                branch 'dev' // only when on dev branch
            }
            steps {
                sh 'git checkout dev' //  change branch to dev
                sh 'git push origin dev:main' // push dev to main
            }
        }
    }
}
