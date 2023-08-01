def abortPreviousRunningBuilds() {
  def hi = Hudson.instance
  def pname = env.JOB_NAME.split('/')[0]

  hi.getItem(pname).getItem(env.JOB_BASE_NAME).getBuilds().each{ build ->
    def exec = build.getExecutor()

    if (build.number != currentBuild.number && exec != null) {
      exec.interrupt(
        Result.ABORTED,
        new CauseOfInterruption.UserInterruption(
          "Aborted by #${currentBuild.number}"
        )
      )
      println("Aborted previous running build #${build.number}")
    } else {
      println("Build is not running or is current build, not aborting - #${build.number}")
    }
  }
}

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
