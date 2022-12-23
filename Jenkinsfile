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
                sh 'docker image build -t nagarjunaduggireddy/saleor-storefrunt:DEV .'
            }
        }
        stage('push image to registry') {
            steps {
                sh 'docker image push nagarjunaduggireddy/saleor-storefrunt:DEV'
            }
        }
    }
}
