pipeline{
    agent any
    //parameters{
        //string(name: "SPEC", defaultValue: "cypress/integration/**/**", description: "Ej: cypress/integration/pageactions.feature")
        //choice(name: "BROWSER", choices:['chrome','edge','safari'], description: "Select browser")
    //}
    options{
        ansiColor('xterm')
    }

    

    stages {
        stage('Build') {
            steps {
                echo "Building application"
            }
        }
        stage('Testing') {
            steps {
                echo "Running tests"
                // Configuración del entorno
                script {
                    def nodePath = sh(script: 'which node', returnStdout: true).trim()
                    env.PATH = "${nodePath}:${env.PATH}"
                }
                sh "/Users/frann/.nvm/versions/node/v18.19.1/bin/npm install"
                sh "npx cypress run"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the app"
            }
        }
}

    // post{
    //     always {
    //         publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: true, reportDir: 'cypress/report', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
    //     }
    // }
}