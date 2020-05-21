pipeline {
   agent any

   stages {
      stage('checkout') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/saikrishna321/contract-testing-boilerplate']]])
         }
      }
      
      stage('Npm Install') {
         steps {
             sh 'npm install'
        }
      }
      
      stage('Run Consumer Test') {
         steps {
             sh 'npm run consumer-service-pact'
        }
      }
      
      stage('Publish Consumer Pact to Pact Broker') {
         steps {
             sh 'node src/rest-api/consumer/consumerPactPublish.js'
        }
      }
   }
   
   
}
