pipeline{
    agent any
    stages{
        stage('prova variabili'){
            steps{
                VERSIONE=bat "(gc versions.yaml | findstr 'version=') -replace 'version=', ''"
                echo VERSIONE
                #bat "echo ((gc versions.yaml) -replace '2.0', '3.0') > versions.yaml"
            }
        }
    }
}