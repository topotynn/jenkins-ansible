pipeline {
    agent {
      label 'ansible'
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: "10"))
        timeout(time: 30, unit: "MINUTES")
        ansiColor("xterm")
        timestamps()
    }
    stages {
        stage("Ansible Job") {
            steps {
                dir("production") {
                    ansiblePlaybook(
                        playbook: './playbook.yml',
                        inventory: env.TARGET,
                        extraVars: [
                            roles_path: './roles',
                            service_name: env.SERVICE_NAME,
                            service_dir: env.SERVICE_DIR
                            ],
                            tags: 'careers-api',
                            credentialsId: env.ANSIBLE_CREDENTIALS_ID,
                    )
                }
            }
        }
    }
}
