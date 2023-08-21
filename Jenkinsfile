pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code from GitHub repository"
                git branch: 'main', url: 'https://github.com/giridharpatnaik183/BasicRemoteTomcatDeployTesting.git'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo "Copying index.html to remote Tomcat server"
                sh 'scp index.html tomcat@18.234.157.123:/path/to/tomcat/webapps/ROOT/'

                echo "Restarting Tomcat on the remote server"
                sh 'ssh tomcat@18.234.157.123 "sudo service tomcat restart"'
            }
        }
    }
}
