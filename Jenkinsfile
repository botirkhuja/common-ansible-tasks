pipeline {
    agent any

    environment {
        EXTERNAL_HDD_UUID = credentials('external_hdd_uuid')
        UBUNTU_WITH_GPU_PASS= credentials('ubuntu_with_gpu_pass')
    }

    stages {
        stage('Build') {
            steps {
              ansiblePlaybook credentialsId: 'jenkins-agent-ansible-generated-key',
                  disableHostKeyChecking: true,
                  installation: 'ansible',
                  // sudoUser: 'ubuntu',
                  inventory: 'inventory.yaml',
                  playbook: 'playbook.yaml'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test commands here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment commands here
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages.'
        }
    }
}