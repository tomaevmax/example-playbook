pipeline {
    agent {label 'ansible'}
    stages {
        stage('prepare') {
            steps {
                git credentialsId: '30cefb5f-0258-4259-9ccd-b9f24d413247', url: 'https://github.com/tomaevmax/example-playbook.git'
            }

        }
        stage('install') {
            steps {
                sh 'pip3 install molecule'
                sh 'pip3 install molecule-docker'
                sh 'pip3 install "urllib3<2.0"'
           }
        }  
        stage('run test') {
            steps {
                dir('roles/java') {
                sh 'molecule test -s default'
                }
            }
        }
    }
}
