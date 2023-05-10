pipeline {
    agent { label 'master' }
    
    options {
        buildDiscarder(logRotator(numToKeepStr:'5'))
        ansiColor('xterm')
    }
    stages {
        stage('Clone repository'){
            steps {
                deleteDir()
                git url: 'https://github.com/VitaliGet/myproject.git', branch: 'master'
            }
        }
        stage('Checking repository'){
            steps {
                sh "ls -l"
            }
        }
        stage('Lint dockerfile'){
            agent {
                docker {
                    image 'hadolint/hadolint:latest-debian'
                    label 'master'
                }
            }
        }
    }
}
