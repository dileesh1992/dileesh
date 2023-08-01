options { disableConcurrentBuilds abortPrevious: true } 


pipeline {
  
    agent any
  
    stages {
       stage('check out scm') {
          steps {
                checkout scm
             }
       }
       stage('Build') {
          steps {
                sleep 10
                }
            }
        }
}
