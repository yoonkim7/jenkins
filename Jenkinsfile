	
	node('master'){
	    stage('import'){
	        try{
                git url:'https://github.com/yoonkim7/jenkins.git'
            }
            catch{
                //slackSendmessage:{env.BUILD_NUMBER} color: 'danger'
            }
            
	    }
	    stage('build'){
	       try{

            }
            catch{
                //slackSendmessage: color: 'danger'
            }
   
	    }
        
	    stage('analyze'){
           try{

            }
            catch{
                //slackSendmessage: color: 'danger'
            }

	    }
	    stage('package'){
             try{

            }
            catch{
                //slackSendmessage: color: 'danger'
            }
	        
	    }
	    stage('deploy'){
          try{

            }
            catch{
                //slackSendmessage: color: 'danger'
            }
	        
	    }
}