 pipeline{
    agent any
    stages{
        stage('Git-checkout'){
            steps{
                git 'https://github.com/babu-alt/indedx.git'
            }
        }
        stage('Maven Build'){
            agent{label "Node"}
            steps{
                sh "mvn clean package"
            }
        }
    }
}
