pipeline{
    agent any
    stages{
        stage('prova variabili'){
            steps{
                //bat "echo ((gc versions.yaml) -replace '2.0', '3.0') > versions.yaml"
                script {
                    env.VERSIONE = bat(script:"(gc versions.yaml | findstr 'version=') -replace 'version=', ''", returnStdout: true).trim()
                   // if you access environment variable in the batch command
                    echo VERSIONE
                }
            }
        }
    }
}