pipeline{
    agent any
    stages{
        stage('Exit if updated'){
            steps{
                script{
                    powershell "git log -1'"
                    //LAST_COMM = powershell(script:"git log -1 | findstr 'version_update'", returnStdout: true).trim()
                    //echo LAST_COMM
                }
            }
        }
        stage('Version Update'){
            steps{
                
                script {
                    env.VERSIONE_OLD = powershell(script:"((gc versions.yaml | findstr 'version=') -replace 'version=', '')", returnStdout: true).trim()
                    env.VERSIONE_NEW = powershell(script:"[string]([double]((gc versions.yaml | findstr 'version=') -replace 'version=', '') + 0.1)", returnStdout: true).trim()
                   // if you access environment variable in the batch command
                    echo VERSIONE_OLD
                    echo VERSIONE_NEW
                    powershell "echo ((gc versions.yaml) -replace '"+VERSIONE_OLD+"', '"+VERSIONE_NEW+"') > versions.yaml"
                    powershell "gc versions.yaml"
                    powershell "git add versions.yaml"
                    powershell "git commit -m 'version_update "+VERSIONE_OLD+"-->"+VERSIONE_NEW+"'"
                    powershell "git push origin HEAD:main"
                }
            }
        }

        stage('Version check'){
            steps{
                echo VERSIONE_OLD
                echo VERSIONE_NEW
            }
        }        
    }
}