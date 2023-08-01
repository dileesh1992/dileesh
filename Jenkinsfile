def buildNumber = env.BUILD_NUMBER as int
for (int i = 1; i < buildNumber; i++)
{
    milestone(i)
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
