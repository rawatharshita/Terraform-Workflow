pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -out=tfplan'
            }
        }
        
        stage('Linting and Static Analysis') {
            steps {
                sh 'terraform fmt -check=true -diff=true'
                sh 'tflint'
            }
        }
        
        stage('Automated Tests') {
            steps {
                // Run your automated tests here (e.g., Terratest)
            }
        }
        
        stage('Terraform Apply') {
            when {
                expression { currentBuild.changeSets != null }
            }
            steps {
                sh 'terraform apply -auto-approve tfplan'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
