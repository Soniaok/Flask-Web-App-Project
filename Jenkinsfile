pipeline {
    agent none
    stages {
        stage('Clone Repo and Build the Flask App') {
            agent {
                label 'node2'
            }
            steps {
                echo 'Clone and Build'
                script {
                    // Clone and Build the Flask App
                    ansiblePlaybook(
                        playbook: '/home/ubuntu/Flask-Web-App-Project/03-centos-ubuntu.yml',
                        inventory: '/home/centos/Flask-Web-App-Project/hosts.ini'
                    )
                }
            }
        }
        stage('Deploy the Flask App with Ansible') {
            agent {
                label 'node2'
            }
            steps {
                echo 'Start the Flask App'
                script {
                    // Start the Flask app
                    ansiblePlaybook(
                        playbook: '/home/centos/Flask-Web-App-Project/04-deploy-centos-ubuntu.yml',
                        inventory: '/home/centos/Flask-Web-App-Project/hosts.ini'
                    )
                }
            }
        }
    }
}
