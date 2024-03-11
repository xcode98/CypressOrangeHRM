pipeline{
    agent any
    //parameters{
        //string(name: "SPEC", defaultValue: "cypress/integration/**/**", description: "Ej: cypress/integration/pageactions.feature")
        //choice(name: "BROWSER", choices:['chrome','edge','safari'], description: "Select browser")
    //}
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
                    nodejs(nodeJSInstallationName: 'Node 18.19.1', configId: 'idConfigNPM') {
                    sh 'npm config ls'
                    }
                    
                    // Asegúrate de instalar las dependencias antes de ejecutar los tests
                    sh "npm install" // o sh "npm install || exit 1" si prefieres mantener el exit 1
                    sh "npx cypress run"
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