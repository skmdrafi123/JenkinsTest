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
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "skmdrafi9492", url: "" ]) {
          sh  'docker push skmdrafi9492/jenkinstest:latest'
          sh  'docker push skmdrafi9492/jenkinstest:$BUILD_NUMBER' 
        }
                  
          }
        }
     
      
    }
}