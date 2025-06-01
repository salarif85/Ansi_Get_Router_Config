pipeline {
    agent any
    stages {
        stage('Checkout Git') {
            steps {
                git branch: 'main', 
                url: 'https://github.com/salarif85/Ansi_Get_Router_Config.git'
            }
        }
        stage('Deploy Config') {
            steps {
                ansiblePlaybook(
                    playbook: 'get_ios_config.yml',
                    inventory: 'inventory.yml'
                )
            }
        }
    }
    post {
        success {
            slackSend message: "Cisco config deployed successfully!"
        }
        failure {
            slackSend message: "Failed to deploy Cisco config. Check logs!"
        }
    }
}