pipeline{
    agent any
    stages{
        stage('prova variabili'){
            steps{
                
                script {
                    env.VERSIONE_OLD = powershell(script:"((gc versions.yaml | findstr 'version=') -replace 'version=', '')", returnStdout: true).trim()
                    env.VERSIONE_NEW = powershell(script:"[string]([double]((gc versions.yaml | findstr 'version=') -replace 'version=', '') + 0.1)", returnStdout: true).trim()
                   // if you access environment variable in the batch command
                    echo VERSIONE_OLD
                    echo VERSIONE_NEW
                    powershell "echo ((gc versions.yaml) -replace '"+VERSIONE_OLD+"', '"+VERSIONE_NEW+"') > versions.yaml"
                    powershell "git status"
                    //powershell "git add ."
                    //powershell "git commit -m '"+VERSIONE_OLD+"-->"+VERSIONE_NEW+"'"
                    //powershell "git push"
                }
            }
        }
    }
}