pipeline {
  agent any

  environment {
    TF_IN_AUTOMATION = "true"
    KUBECONFIG = "${HOME}/.kube/config"
  }

  tools {
    terraform 'Terraform'
  }

  stages {

    stage('Checkout Repository') {
      steps {
        checkout scm
      }
    }


    stage('Deploy with Terraform') {
      steps {
        dir('.') {
          sh 'sudo terraform init'
          sh 'sudo terraform apply -auto-approve'
        }
      }
    }
  }

  post {
    success {
      echo "✅ Déploiement réussi via Terraform et images récupérées"
    }
    failure {
      echo "❌ Échec du déploiement"
    }
  }
}
