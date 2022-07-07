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
                        credentialsId: "uharov_key",
                        inventoryContent: env.TARGET
//                        extraVars: [
//                            target: env.TARGET
//                        ]
                    )
                }
            }
        }
    }
}
