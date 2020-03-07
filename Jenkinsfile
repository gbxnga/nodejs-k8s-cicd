pipeline { 
    agent any 
    stages {
        stage('Build') { 
            steps { 
                sh "echo 'building..'"
            }
        }
        stage('Test'){
            steps {
                sh "echo 'Testing...'"
                sh "echo 'Testing2...'" 
            }
        }
        stage('Deploy') {
            steps {
                sh "echo 'Deploying...'"
                sh "echo 'Deploying 2...'"
            }
        }
    }
}