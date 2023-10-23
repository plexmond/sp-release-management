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
                branch 'dev' // Voer deze stap alleen uit op de 'dev'branch
            }
            steps {
                input 'Keur de wijzigingen goed om naar main te pushen?' // handmatige goedkeuring
            }
        }

        stage('Push to Main') {
            when {
                branch 'dev' // voer stap alleen uit op de dev branch
            }
            steps {
                sh 'git push origin dev:main' // push van dev naar main
            }
        }
    }
}