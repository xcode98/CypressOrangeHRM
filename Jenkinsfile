pipeline{
    agent any
    //parameters{
        //string(name: "SPEC", defaultValue: "cypress/integration/**/**", description: "Ej: cypress/integration/pageactions.feature")
        //choice(name: "BROWSER", choices:['chrome','edge','safari'], description: "Select browser")
    //}

    tools {
        nodejs 'node' // Cambiado de 'node' a 'nodejs'
    }

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
                
                sh "npm install"
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