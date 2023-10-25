pipeline {
    agent any
    triggers {
        pollSCM('H/5 * * * *')
    }
    stages {
        stage('Delete existing files') {
            steps {
                script {
                    def serverHost = '10.0.10.22'
                    def serverUser = 'student'

                    // delete existing
                    sshagent(['ssh-id']) {
                        sh "ssh -v ${serverUser}@${serverHost} sudo rm -rf /var/www/html/*"
                    }
                }
            }
        }

        stage('Deploy files to webserver') {
            steps {
                script {
                    // server
                    def serverHost = '10.0.10.22'
                    def serverUser = 'student'
                    def remotePath = '/var/www/html/'

                    // copy repo
                    sshagent(['ssh-id']) {
                        sh "scp -r ./* ${serverUser}@${serverHost}:${remotePath}"
                    }
                }
            }
        }
    }
}
