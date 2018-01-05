	
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
//	    stage('test'){
//             try{
 //               dir('JenkinsMVC.Test'){
 //                   bat 'dotnet restore'
 //                   bat 'msbuild /t:build JenkinsMVC.Tests.csproj'
 //                   bat 'dotnet test'
 //               }
 //           }
 //           catch(error){
 //               //slackSendmessage: color: 'danger'
 //           }
	        
//	    }
         stage('package'){
             try{
                 dir('JenkinsMVC'){
                   //  bat 'msbuild /t:pack JenkinsMVC.csproj'
                    bat 'dotnet publish JenkinsMVC.csproj --output ../Package'
                 }
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    }
	    stage('deploy'){
          try{
              //p:computer= dnsawc -p:username=admin -p:password= the passwordkeything with """                                                    workspace\JenkinsPipeLine\JenkinsMVC\bin\Debug\netcoreapp2.0\                                                       C:\Program Files (x86)\Jenkins\workspace\JenkinsPipeLine
          //    '"C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:iisApp="C:\\Program Files (x86)\\Jenkins\\workspace\\JenkinsPipeLine\\Package\\JenkinsOps\\obj\\Debug\\netcoreapp2.0\\PubTmp\\Out" -dest:iisApp="Default Web Site/jenkinsops" -p:computer= -p:username= -p:password=  -enableRule:AppOffline'

            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    }
}