pipeline{
    agent any
    
    tools{
    maven 'mymaven'
    }
stages{
    stage('CloneRepo'){
        steps{
            git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
        }
    }
    stage('CompileCode'){
        steps{
            echo 'Compiling ..'
            sh 'mvn compile'
        }
    }
     stage('Review Code'){
        steps{
            echo 'Reviewing..'
            sh 'mvn pmd:pmd'
        }
    }
   stage('TestCode'){
       steps{
           sh 'mvn test'  
       }
       post{
          always{
              echo 'Convert test reports'
          }
          success{
          junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
          }
       }
   }
    stage('PackageCode'){
        steps{
            sh 'mvn clean package'
        }
    }
}

}

