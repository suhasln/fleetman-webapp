def label = "mypod-${UUID.randomUUID().toString()}"
def name = 'jenkins'

podTemplate(label: 'label', containers: [
    containerTemplate(name: 'git', image: 'alpine/git', ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'kubectl', image: 'suhasln/kubectl', command: 'cat', ttyEnabled: true)
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
  ]
  ) { 
    environment {

     ORGANIZATION_NAME = "suhasln"
     YOUR_DOCKERHUB_USERNAME = "suhasln"
     
     SERVICE_NAME = "fleetman-webapp"
     REPOSITORY_TAG="${YOUR_DOCKERHUB_USERNAME}/${ORGANIZATION_NAME}-${SERVICE_NAME}:${BUILD_ID}"
   }

    node('label') {

        stage('Preparation') {
         steps {
            cleanWs()
            git credentialsId: 'GitHub', url: "https://github.com/${ORGANIZATION_NAME}/${SERVICE_NAME}"
         }
      }
        
         stage('Build') {
         steps {
            sh 'echo No build required for Webapp.'
         }
      }

        stage('Deploy to Cluster') {
          steps {
            sh 'envsubst < ${WORKSPACE}/deploy.yaml | kubectl apply -f -'
          }
      }
    }
}
