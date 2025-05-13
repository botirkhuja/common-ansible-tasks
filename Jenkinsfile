pipeline {
    agent {
      label 'jenkins-ubuntu-agent'
    }

    environment {
        EXTERNAL_HDD_UUID = credentials('external_hdd_uuid')
        UBUNTU_WITH_GPU_PASS= credentials('ubuntu_with_gpu_pass')
    }

    stages {
        stage('Run Ansible Playbook') {
            steps {
              ansiblePlaybook credentialsId: 'jenkins-agent-ansible-generated-key',
                  disableHostKeyChecking: true,
                  // installation: 'ansible',
                  become: true,
                  sudoUser: 'botir',
                  // becomeUser: 'botir',
                  inventory: 'inventory.yaml',
                  playbook: 'playbook.yaml'
                  colorized: true,
                  // forks: 2,
                  // startAtTask: '004',
                  // tags: 'deploy',
                  // vaultCredentialsId: 'external_hdd_uuid',
                  // vaultTmpPath: ''
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages.'
        }
    }
}