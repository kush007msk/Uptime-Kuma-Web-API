pipeline {
    agent any

    parameters {
        choice(
            name: 'action',
            choices: ['up', 'down','setup'],
            description: 'Please select the action to build'
        )
    }

    stages {
        stage('Git Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/kush007msk/Uptime-Kuma-Web-API.git' // Use ':' instead of ',' in key-value pairs
            }
        }

        stage('Deploy uptime-kuma into k8s') {
            steps {
                sh """
                   cd \${WORKSPACE} # Use \${WORKSPACE} to refer to the workspace
                   make \${action} & # Use \${action} to reference the parameter
                """
            }
        }
    }
}
