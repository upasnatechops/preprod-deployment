#!/usr/bin/env groovy

pipeline {

  agent any
  stages {
    stage('Deploy') {
      agent {
        label "kubectl"
      }
      steps {
        container('kubectl') {
          sh 'which kubectl'
	script {
            def repo_name = env.JOB_NAME
            def branch_name = env.BRANCH_NAME
              
            sh """
             
            echo "Changes seen in repo " $repo_name " in branch" $branch_name
			####kubectl delete namespace preprod-es-mongo
			#sleep 30
            kubectl apply -f ./"$branch_name"
            """
          }
        }
       }

    }

 }
}
