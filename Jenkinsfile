pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('git') { 
            steps { 
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/DanyshMushtaq/WindowsUpdateWithAnisble.git]]])
            }
        }
       stage('Tools Init') {
            steps {
                script {
                 sh 'ansible --version'
            }
            }
        }
        stage('playbook') {
            steps{
                ansiblePlaybook credentialsId: 'fc36434a-e8ed-4f82-83dd-6ec29e312aad', disableHostKeyChecking: true, inventory: 'hosts', playbook: 'windowsupdate.yml'
                }
            }
    }
    
}
