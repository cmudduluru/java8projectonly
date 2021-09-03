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

            git --version
            '''
         }
		}
	 }
    }
}  
  
