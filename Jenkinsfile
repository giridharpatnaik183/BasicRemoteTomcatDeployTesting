pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/path/to/tomcat/webapps' // Set this to the actual path of the Tomcat webapps directory
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                checkout scm
            }
        }

        stage('Copy HTML to Tomcat') {
            steps {
                script {
                    def tomcatWebappsDir = "${TOMCAT_WEBAPPS}/ROOT/"
                    sh "cp index.html ${tomcatWebappsDir}"
                }
            }
        }

        stage('Restart Tomcat') {
            steps {
                script {
                    // Restart Tomcat on the remote server (adjust the command as needed)
                    sh 'ssh tomcat@18.234.157.123 "sudo service tomcat restart"'
                }
            }
        }
    }
}
