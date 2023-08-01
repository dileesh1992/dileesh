def buildNumber = env.BUILD_NUMBER as int
if (buildNumber > 1) {
    milestone(buildNumber - 1)
}
milestone(buildNumber)


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
