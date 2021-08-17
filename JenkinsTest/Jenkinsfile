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
     stage('Run Docker container on Jenkins Agent') {
             
            steps {
                sh "docker run -d -p 4030:80 skmdrafi9492/jenkinstest"
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 4001:80 skmdrafi9492/jenkinstest"
 
            }
        }
      
    }
}