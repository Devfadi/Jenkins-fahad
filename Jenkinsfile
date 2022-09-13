
pipeline {
   agent any
  parameters{
    choice(name: 'Version', choices:['1.1.1','1.1.2','1.1.3'], description:'')
    booleanParam(name: 'testing', defaultValue:true, description:'')
  }
  environment {
    imagename = "haroon-image"
  }
 
  stages {
   
    stage('echos') {
      steps {
        
        echo "${workspace}"
        echo "${BUILD_NUMBER}"
        echo "${WORKSPACE_TMP}"
        echo "${JENKINS_URL}"
      }
    }

    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/Devfadi/Jenkins-fahad.git', branch: 'main'])

      }
    }

    stage('version') {
      steps {
        sh 'pwsh --version'

      }
    }

    stage('Building image') {
      steps{
        script {
          sh "pwsh docker build -t ${imagename}:latest ."
          // sh "sudo docker build -t ${imagename}:latest ."
         // powershell 'docker-compose up'
        }
      }
    }
    stage('Docker Build container') {
      
      steps {
        
        dir('../git-dockers') {
            sh 'pwsh docker-compose up'
           //sh 'docker-compose up'
        }
        // powershell 'docker-compose up'
            
      }
    }

  }
}
