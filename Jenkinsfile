pipeline {
agent any
stages {

 stage('pull artifact') {
            steps {
                copyArtifacts filter: '**/', fingerprintArtifacts: true, 
			projectName: '${JOB_NAME}', 
				selector: specific('${BUILD_NUMBER}'),
			     target: 'prereq'
            }
        }
		
stage('Deploy CloudHub') {
steps {
echo 'Deploying mule project'
echo 'Deploying to the configured environment….'
bat 'mvn package deploy -DmuleDeploy -Dusername=pavan4030 -Dpassword=gayiChittu@123 -Denv=dev -DworkerType=Micro -Dworkers=1 -DcloudHub.Environemnt=TEST -Dregion=us-east-1' 
}
}
}
}
