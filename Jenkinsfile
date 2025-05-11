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
                  installation: 'botir',
                  sudoUser: 'botir',
                  inventory: 'inventory.yaml',
                  playbook: 'playbook.yaml'
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages.'
        }
    }
}