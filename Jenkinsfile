pipeline{
    agent any
    parameters{
        string(name: "SPEC", defaultValue: "cypress/integration/**/**", description: "Ej: cypress/integration/pageactions.feature")
        choice(name: "BROWSER", choices:['chrome','edge','safari'], description: "Select browser")
    }
    options{
        ansiColor('xterm')
    }

    stages{
        stage('Build'){
            steps{
                echo "Building application"
            }
        }
        stage('Testing'){
            steps{
                echo "Running tests"
                // Configuración del entorno
                    env.PATH = "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"
                    
                    // Asegúrate de instalar las dependencias antes de ejecutar los tests
                    sh "npm ci" // o sh "npm install || exit 1" si prefieres mantener el exit 1
                    sh "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
            }
        }
        stage('Deploy'){
            steps{
            echo "Deploying the app"
            }
        }
    }
    
}

post{
    always {
        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: true, reportDir: 'cypress/report', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
    }
}