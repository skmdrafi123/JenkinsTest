pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t jenkinstest:latest .' 
                sh 'docker tag jenkinstest skmdrafi9492/jenkinstest:latest'
                sh 'docker tag jenkinstest skmdrafi9492/jenkinstest:$BUILD_NUMBER'
               
          }
        }
    
      
    }
}