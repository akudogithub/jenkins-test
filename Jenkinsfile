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
        stage('system-check'){
            steps{
                sh 'lsblk'
            }
        }
        stage('ram-check'){
            steps{
                sh 'free -g'
                sh 'free -m'
            }
        }
        stage('regression-test1'){
            parallel{
                stage('test-1e'){
                    steps{
                        sh 'echo "running reg-test 1e'
                    }
                }
                stage('test-1b'){
                    steps{
                        sh 'echo "running reg-test 1c'
                    }
                }
            }
        }
        stage('check-user'){
            steps{
                sh 'cat /etc/passwd'
            }
        }
    }
}