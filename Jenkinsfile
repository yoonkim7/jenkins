	
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
                    bat 'dotnet publish JenkinsMVC.csproj'// --output ../Package'
                 }
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    }
	    stage('deploy'){
          try{//-p:computer=ec2-54-165-189-15.compute-1.amazonaws.com -p:username=admin -p:password=T;RfM*zCOnjBniVKDPm$*zBH-in5@%(9
              //p:computer= dnsawc -p:username=admin -p:password= the passwordkeything with """                                                    workspace\JenkinsPipeLine\JenkinsMVC\bin\Debug\netcoreapp2.0\                                                       C:\Program Files (x86)\Jenkins\workspace\JenkinsPipeLine

                   bat 'dotnet build ./JenkinsMVC/JenkinsMVC.csproj /p:DeployOnBuild=true /p:PublishProfile=publish.pubxml'
                //    bat 'msdeploy -verb:sync -source:iisApp="C:\\Program Files (x86)\\Jenkins\\workspace\\JenkinsPipeLine\\Package\\" -dest:iisApp="Default Web Site/NAMEOFPROJECT" ,computername="ec2-54-165-189-15.compute-1.amazonaws.com",username="Administrator",password="T;RfM*zCOnjBniVKDPm$*zBH-in5@%(9"  -enableRule:AppOffline'

                    bat 'msdeploy -verb:sync -source:iisApp=\"C:\\Program Files (x86)\\Jenkins\\workspace\\JenkinsPipeLine\\Package\\" -dest:iisApp="Default Web Site/NAMEOFPROJECT",computername="ec2-54-165-189-15.compute-1.amazonaws.com",username="ADMINISTRATOR",password="T;RfM*zCOnjBniVKDPm$*zBH-in5@%(9" -enableRule:AppOffline'
              
            }
            catch(error){
                //slackSendmessage: color: 'danger'
            }
	        
	    }
}