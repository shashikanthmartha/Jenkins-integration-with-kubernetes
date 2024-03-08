pipeline {

  environment {
    dockerimagename = "shashikanthmartha/nodeapp"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/shashikanthmartha/nodeapp_test.git'
      }
    }

    // stage('Build image') {
    //   steps{
    //     script {
    //       dockerImage = docker.build dockerimagename
    //     }
    //   }
    // }

    // stage('Pushing Image') {
    //   environment {
    //            registryCredential = 'dockerhublogin'
    //        }
    //   steps{
    //     script {
    //       docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
    //         dockerImage.push("v1")
    //       }
    //     }
    //   }
    // }

    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
        }
      }
    }

  }

}
