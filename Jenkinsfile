pipeline{
  agent none

  stages{
    stage('Checkout'){
      agent any
      steps{
        git 'https://github.com/RaguraamanVM/jenkins-docker-as-agents-multi-stage-ci.git'
      }
    }
  
    stage('Backend Build - maven'){
      agent{
        docker{
          image 'maven:3.8.1-openjdk-11'
          args '-v /root/.m2:/root/.m2'
        }
      }
      steps{
        dir('backend'){
          sh 'mvn clean package'
        }
      }
    }

    stage('Frontend Build - nodejs'){
      agent{
        docker{
          image 'node:16-alpine'
        }
      }

      steps{
        dir('frontend'){
          sh 'npm install'
          sh 'npm start'
        }
      }
    }

    stage('Both stages combine'){
      agent any
      steps{
        echo "Both Backend and frontend stages completed"
      }
    }
  }
}


    
    
      
        
        
  
      
