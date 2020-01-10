node{
	def COMMITER_EMAIL = ""
    stage('checkout'){
    	steps{
    		COMMITER_EMAIL = sh(script: "git --no-pager show -s --format='%%ae'",
    			returnStdout: true).split('\r\n')[2].trim()
    		echo "COMMITER_EMAIL: ${COMMITER_EMAIL}"
    	}
	}
}
