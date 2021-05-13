def remote = [:]
remote.name = 'test'
remote.host = '18.209.247.127'
remote.port = 22
remote.allowAnyHosts = true

pipeline {
    agent any

    stages {
        stage('Pulling') {
            steps {
                git branch: 'main', credentialsId: '10045992-3c80-4957-83dc-5c3c79659723', url: 'https://github.com/anindyadas93/apache2.git'
                //sh 'unzip -o test.zip'
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'ubuntu-ec2', passwordVariable: 'pass', usernameVariable: 'user')]) {
                        remote.user = user
                        remote.password = pass
                        //sshRemove remote: remote, path: "/var/www/html/index.html"
                        sshPut remote: remote, from: 'index.html', into: '/var/www/html/'
                    }
                }
            }
        }
    }
}

