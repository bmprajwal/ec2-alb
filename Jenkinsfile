pipeline {
    agent any

    environment {
        // Optionally, set AWS credentials here or configure them on Jenkins node
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id2')
         AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key2')
    }

    stages {
        stage('Checkout Terraform Code') {
            steps {
                git branch: 'main', url: 'https://github.com/bmprajwal/ec2-alb.git'
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

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve tfplan'
            }
        }
    }
}
