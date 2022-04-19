@Library('keptn-library@3.5')_
def keptn = new sh.keptn.Keptn()

pipeline {
   agent any

   environment {
     // You must set the following environment variables
     ORGANIZATION_NAME = 'suhasln'
     YOUR_DOCKERHUB_USERNAME = 'suhasln'
     
     SERVICE_NAME = "webapp"
     REPOSITORY_TAG="${YOUR_DOCKERHUB_USERNAME}/${ORGANIZATION_NAME}-${SERVICE_NAME}:${BUILD_ID}"
   }

   stages {
     /* stage('Preparation') {
         steps {
            cleanWs()
            git credentialsId: 'GitHub', url: "https://github.com/${ORGANIZATION_NAME}/${SERVICE_NAME}"
         }
      } */
      
      stage('Add Dependencies') {
         steps {
            sh 'cat /etc/issue'
         }
      }
      
      stage('Download Kubectl & Config') {
         steps {
            sh 'echo No build required for Webapp.'
            sh 'curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.21.11/bin/linux/amd64/kubectl'
            sh 'chmod +x ./kubectl'
            sh './kubectl version --client'
         }
      }
      
      stage('Download Helm') {
         steps {
            sh 'echo No build required for Webapp.'
            sh 'curl -LO https://get.helm.sh/helm-v3.6.0-linux-amd64.tar.gz'
            sh 'tar xvf helm-v3.6.0-linux-amd64.tar.gz'
            sh 'linux-amd64/helm version'
         }
      }

     /* stage('Build Image') {
         steps {
           sh 'docker image build -t ${REPOSITORY_TAG} .'
         }
      } */
      
      stage('Test Image') {
         steps {
           sh 'echo "Testing..."'
         }
      }
      
      stage('Push Image') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }
      
      stage('Deploy to Dev Environment') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }
      
      stage('Run Load Tests') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }
      
      stage('Deploy To Pre-Prod') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }
      
      stage('Integration Tests') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }
      
      stage('Release') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }

      stage('Deploy to Production') {
          steps {
            sh './kubectl --kubeconfig=./config apply -f deploy.yaml'
          }
      }
      
      stage('Run Smoke Tests') {
         steps {
           sh 'echo "Image is pushed to the docker repository."'
         }
      }
   }
}
