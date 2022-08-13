def gv

pipeline{
  
  agent any
  parameters{
    choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: '')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }
  stages{
    
    stage("init"){
      
      steps{
        script{
          gv = load"script.groovy"
        }
      }
    }
    
    stage("Build"){
      
      steps{
        script{
          gv.buildApp()
        }
      }
    }
    
    stage("Test"){
      when {
        expression{
          params.executeTests
        }
      }
      steps{
        script{
          gv.testApp()
        }
      }
    }
    
    stage("Deploy"){
//       input {
//         message"Select the environmentn to deploy to"
//         ok "Done"
//         parameters{
//           choice(name: 'ONE', choices: ['dev','staging','prod'], description: '')
//           choice(name: 'TWO', choices: ['dev','staging','prod'], description: '')
//         }
//       }
      steps{
        script{
          env.ENV = input message: "Select the environmentn to deploy to", ok: "Done", parameters: [choice(name: 'ONE', choices: ['dev','staging','prod'], description: '')]
          
          gv.deployApp()
          echo "Deploying to ${ENV}"
//           echo "Deploying to ${TWO}"
        }
      }
    }
    
  }
}
