pipeline {
  agent {label 'storefrunt'}
    triggers {
       // pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git branch: 'canary', url: 'https://github.com/nagarjuna33/react-storefront.git'
            }
        }
        stage('docker image build') {
            steps {
                sh 'docker compose build '
                sh 'docker image tag storefront nagarjunaduggireddy/storefront:DEV .'
                sh 'docker image tag saleor-app-checkout nagarjunaduggireddy/saleor-app-checkout:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker image push nagarjunaduggireddy/storefront:DEV'
                 sh 'docker image push nagarjunaduggireddy/saleor-app-checkout:DEV'
            }
        }
    }
}
