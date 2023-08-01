pipeline {
    agent any
    stages {
        stage('Trigger New Build') {
            steps {
                // Trigger the new build
                build job: "test"
            }
        }
        stage('Cancel Old Builds') {
            steps {
                script {
                    // Wait for a few seconds to ensure the new build starts
                    sleep 5

                    // Get the current build number
                    def currentBuildNumber = env.BUILD_NUMBER

                    // Get the list of old build numbers
                    def oldBuildNumbers = sh(
                        script: "jenkins-cli get-builds ${JOB_NAME} | grep \"#[0-9]\" -o | grep -v \"#${currentBuildNumber}\" | grep \"[0-9]\" -o",
                        returnStdout: true
                    ).trim().split('\n')

                    // Cancel old builds if they are running
                    oldBuildNumbers.each { buildNumber ->
                        sh "jenkins-cli stop-build ${JOB_NAME} ${buildNumber}"
                        echo "Old build ${buildNumber} canceled."
                    }
                }
            }
        }
    }
}
