pipeline{
    agent any
    stages{
        stage('git-clone'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/akudogithub/jenkins-test.git']])
            }
        }
        stage('cpu-check'){
            steps{
                sh 'lscpu'
            }
        }
        stage('security-check'){
            steps{
                sh 'bash /var/lib/jenkins/workspace/jenkins-test-pipeline/security.sh'
            }
        }
    }
}