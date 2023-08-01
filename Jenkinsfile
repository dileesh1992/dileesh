pipeline {
    
    agent any
    
    stages {
        stage('Trigger New Build') {
            steps {
                // Trigger the new build
                build job: env.JOB_NAME
            }
        }
        
        stage('Cancel Old Builds') {
            steps {
                script {
                    // Wait for a few seconds to ensure the new build starts
                    sleep 5

                    // Get the current build number
                    def currentBuildNumber = env.BUILD_NUMBER.toInteger()

                    // Get the list of all builds of the current job
                    def allBuilds = Jenkins.instance.getItemByFullName(env.JOB_NAME).builds

                    // Cancel any old builds that are running and older than the current build
                    allBuilds.each { build ->
                        if (build.number.toInteger() != currentBuildNumber && build.isBuilding()) {
                            sh "curl -X POST ${env.JENKINS_URL}/job/${env.JOB_NAME}/${build.number}/stop"
                            echo "Old build ${build.number} canceled."
                        }
                    }
                }
            }
        }
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
