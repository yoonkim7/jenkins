	
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
                   bat 'dotnet restore'
                   bat 'msbuild /t:clean,rebuild JenkinsMVC.csproj'
               }
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
   
	    }
        
	    stage('analyze'){
           try{
               dir('JenkinsMVC'){
                   bat 'C:\\Tools\\SonarQube\\SonarQube.Scanner.MSBuild.exe begin /k:kimylol'
                   bat 'msbuild /t:rebuild JenkinsMVC.csproj'
                   bat 'C:\\Tools\\SonarQube\\SonarQube.Scanner.MSBuild.exe end'
               }
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