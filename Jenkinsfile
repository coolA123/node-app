pipeline{
    agent any
     stages {
        stage('Git Checkout') {
          steps {
            echo "Checkout Stage"
            checkout scm
          }
        }
        stage('Building Docker Image'){
            steps{
                echo 'Building Stage'
                sh 'docker --version'
            }
        }
        stage('Deploy'){
            steps{
            	echo "Deploy Stage"
		sh "eval \$(aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/a2u9gj4)"
                sh "docker build . -t upgradAditya-assignment"
                sh "docker push public.ecr.aws/a2u9gj4/upgradAditya:latest"
            }
        }
     }
}
