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
                        credentialsId: "36745364-f4af-4aa5-be8d-08169ced78dc",
                        extraVars: [
                            target: env.TARGET
                        ]
                    )
                }
            }
        }
    }
}
