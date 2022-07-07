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
                    ansiblePlaybook('playbook.yml') {
                    playbook(playbook.yml)
                    ansibleName('uharov_ansible')
                    inventoryPath('ansible_host')
                    credentialsId('36745364-f4af-4aa5-be8d-08169ced78dc')
                    become(true)
                    }
                }
            }
        }
    }
}
