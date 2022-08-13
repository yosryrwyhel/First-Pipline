pipeline{
  
  agent any
  tools{
    maven 'Maven'
  }
  parameters{
    
  }
  stages{
    
    stage("Build"){
      
      steps{
        echo 'Building the application....'
        sh"mvn install"
      }
    }
    
    stage("Test"){
      
      steps{
        echo 'Testing the application....'
      }
    }
    
    stage("Deploy"){
      
      steps{
        echo 'Deploying the application....'
      }
    }
    
  }
}
