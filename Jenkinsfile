pipeline { 
    agent any 
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('git') { 
            steps { 
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/narsingarao529/windowsupdate.git']]])
              //  checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/narsingarao529/windowsupdate.git']]])
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
                //ansiblePlaybook disableHostKeyChecking: true, inventory: 'hosts', playbook: 'windowsupdate.yml'
                //ansiblePlaybook installation: 'ansible', inventory: 'hosts', playbook: 'windowsupdate.yml'
                //ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'windowsupdate.yml'
              // ansiblePlaybook credentialsId: '05f5f5c9-162b-48b2-81c7-ff9d7e4e533f', disableHostKeyChecking: true, installation: 'ansible', inventory: 'hosts', playbook: 'windowsupdate.yml'
                
                }
            }
    }
    
}
