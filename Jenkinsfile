pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/var/lib/tomcat9/webapps' // Set this to the actual path of the Tomcat webapps directory
        REMOTE_SERVER = 'ubuntu@172.31.32.41' // Remote server SSH address and Tomcat remote IP
        TOMCAT_USER = 'tomcat' // Tomcat user on the remote server
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                checkout scm
            }
        }

        stage('Copy HTML to Remote Server') {
            steps {
                script {
                    // Copy index.html to the remote server
                    sh "scp index.html ${env.REMOTE_SERVER}:${env.TOMCAT_WEBAPPS}/ROOT/"
                }
            }
        }

        stage('Restart Remote Tomcat') {
            steps {
                script {
                    // Restart Tomcat on the remote server
                    sh "ssh ${env.REMOTE_SERVER} 'sudo service tomcat restart'"
                }
            }
        }
    }
}
