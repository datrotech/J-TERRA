pipeline {
    agent any
    
    tools {
        terraform 'terraform_name'  // Fixed: removed space and special characters
    }
    
    stages {
        stage('Git') {
            steps {
                git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/datrotech/J-TERRA.git'
            }
        }
        
        stage('Terraform') {
            steps {
                sh "terraform -v"
                dir('T-Scripts') {  // Fixed: use relative path from workspace
                    sh "terraform init"    
                    sh "terraform plan"
                    // sh "terraform apply --var-file terraform.tfvars --auto-approve"
                    sh "terraform destroy --auto-approve"
                }
            }
        }
    }
}
