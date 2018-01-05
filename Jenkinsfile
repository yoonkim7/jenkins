	
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
                   bat 'C:\\Tools\\SonarQube\\SonarQube.Scanner.MSBuild.exe begin /k:welala'
                   bat 'msbuild /t:build JenkinsMVC.csproj'
                   bat 'C:\\Tools\\SonarQube\\SonarQube.Scanner.MSBuild.exe end'
                   
               }
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }

	    }
	    stage('test'){
             try{
                dir('JenkinsMVC.Test'){
 //                   bat 'dotnet restore'
 //                   bat 'msbuild /t:build JenkinsMVC.Tests.csproj'
 //                   bat 'dotnet test'
                }
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    } stage('package'){
             try{
                 dir('JenkinsMVC'){
                     bat 'msbuild /t:package JenkinsMVC.csproj'
                 }
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