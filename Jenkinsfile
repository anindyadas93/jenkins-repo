pipeline {
    agent any

    stages {
        stage('Pulling') {
            steps {
                git branch: 'main', credentialsId: '10045992-3c80-4957-83dc-5c3c79659723', url: 'https://github.com/anindyadas93/apache2.git'
            }
        }
        stage('Deploy') {
            steps {
                sh 'unzip -o test.zip'
                sh "mv index.html /var/www/html/index.html"
            }
        }
    }
}

