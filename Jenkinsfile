pipeline{
    agent any
    stages{
        stage('prova variabili'){
            steps{
                bat "sed -i 's/version=2.0/version=3.0/' application.yaml"
            }
        }
    }
}