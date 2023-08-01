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
                    sh 'mvn clean package'
                }
            }
        } 
}
