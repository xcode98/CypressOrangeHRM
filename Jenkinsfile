pipeline{
    agent any
    parameters{
        string(name: "SPEC", defaultValue: "cypress/integration/**/**", description: "Ej: cypress/integration/pom/*.spec.js")
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
                sh "npm i"
                sh "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
            }
        }
    }
    stage('Deploy'){
        steps{
            echo "Deploying the app"
        }
    }
}

post{
    always {
        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: true, reportDir: 'cypress/report', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
    }
}