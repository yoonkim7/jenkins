	
	node('master'){
	    stage('import'){
	        try{
                git url:'https://github.com/yoonkim7/jenkins.git'
            }
            catch(error){
                //slackSendmessage:{env.BUILD_NUMBER} color: 'danger'
            }
            
	    }
	    stage('build'){
	       try{
               dir('JenkinsMVC'){
                   bat 'nuget restore'
                   bat 'msbuild /t:clean,rebuild JenkinsMVC.csproj'
               }
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
   
	    }
        
	    stage('analyze'){
           try{

            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }

	    }
	    stage('package'){
             try{
 
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    }
	    stage('deploy'){
          try{

            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    }
}