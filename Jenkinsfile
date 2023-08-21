pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from your GitHub repository
                git branch: 'main', url: 'https://github.com/giridharpatnaik183/BasicRemoteTomcatDeployTesting.git'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                // Copy the index.html file to the Tomcat webapps directory on the remote server
                sh 'scp index.html tomcat@18.234.157.123:/path/to/tomcat/webapps/ROOT/'

                // Restart Tomcat on the remote server
                sh 'ssh tomcat@18.234.157.123 "sudo service tomcat restart"'
            }
        }
    }
}
