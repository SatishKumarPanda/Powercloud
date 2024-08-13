pipeline {
    agent any
    
    tools {
        maven 'maven'
    }
    triggers {
         pollSCM('* * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    emailext body: 'Congragulation your build sucess', subject: 'Success', to: 'satishpanda430@gmail.com'
                }
          failure {
                    emailext body: 'Congragulation your build failure', subject: 'Failure', to: 'satishpanda430@gmail.com'
                }
            }
            }
              stage('Deployment'){
            steps {
                echo 'Sucessfully Deploy'
            }
        }
        
    
            }
}
