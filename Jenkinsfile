def maven_tool = 'mvn' 
pipeline {
  agent any
	tools {
		jdk 'jdk8u161'
	}
  	stages {
   	stage('Build') {
	    steps {
	     withEnv(["MAVEN_HOME=${tool maven_tool}"]) {
			sh '''
			echo ${GIT_BRANCH}
			export PATH=${MAVEN_HOME}/bin:$PATH
			echo "----- Starting ${JOB_BASE_NAME} build -----"
            env

            echo "----- Downloading sub-modules -----"
            git submodule update --init

            echo "----- Updating Project Module Versions -----"

            mvn -N versions:update-child-modules -DgenerateBackupPoms=false

            echo "----- Building ${JOB_BASE_NAME} -----"
            
            mvn clean deploy -U -DdeployAtEnd
            fi
            '''
         }
		}
	 }
    }
}  
  
