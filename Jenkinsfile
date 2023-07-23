pipeline{
    agent any
    stages{
        stage('git-clone'){
            steps{
                sh checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/akudogithub/jenkins-test.git']])
            }
        }
        stage('server-update'){
            steps{
                sh 'sudo apt update -y'
            }
        }
    }
}